A dynamic binary instrumentation tool, that allows hooking to functions and more.
For basic usage (like hooking to system API calls), [[#frida-trace]] is enough.
## Javascript API
Used for the instrumentation script, the actual script interacting with the process.
Full documentation: https://frida.re/docs/javascript-api/
### Function addresses
Library function:
`var ptr = Module.findExportByName("libc.so.6", "name")'`
Binary function:
`var base = Module.findBaseAddress("file_name");`
`var address = base.add(0xoffset);`
You can get `offset` from `objdump`, `Ghidra` or anything else.

### Attaching to a function
```js
Interceptor.attach(functionAddress, {
	onEnter: function(args) {
		console.log("entered");
    },
    onLeave: function(retval) {
        console.log("left");
    }
});
```
### Replacing a function
`Interceptor.replace(functionAddress, nativeCallback);`
Example:
```js
var openPtr = Module.findExportByName("libc.so.6", "open");
var open = new NativeFunction(openPtr, 'int', ['pointer', 'int']);
Interceptor.replace(openPtr, new NativeCallback(function (pathPtr, flags) {
    var path = Memory.readUtf8String(pathPtr);
    log("Opening '" + path + "'");
    var fd = open(pathPtr, flags);
    log("Got fd: " + fd);
    return fd;
}, 'int', ['pointer', 'int']));
```
### NativeFunction and NativeCallback Valid Data Types
- `void`
- `pointer`
- `int`, `uint`
- `long`, `ulong`
- `char`, `uchar`
- `size_t`, `ssize_t`
- `float`, `double`
- `int8`, `int16`, `int32`, `int64`
- `uint8`, `uint16`, `uint32`, `uint64`
- `bool`
### NativePointer
A wrapper to a memory address.
#### As number
Note that number parameters to functions are the number itself wrapped in a NativePointer.
To read as int: `{NativePointer}.toInt32()`
To assign: `{NativePointer} = ptr(123);`
#### Reading and writing from memory
In order to read, use `{NativePointer}.read<data type name>()`
In order to write to a location you can similarly use `{NativePointer}.write<data type name>()`
where `<data type name>` is replaced with the name of the data type.

Note that strings should be allocated to a new position instead of written directly because the string may reside in read-only memory or be longer than the allocated space.
This can be done using:
```js
const buf = Memory.allocUtf8String('mystring');
this.buf = buf;
args[0] = buf;
```
##### List of types
- `CString` (mostly equivalent to `Utf8String`. can't be allocated, use `allocateUtf8String`)
- `Utf8String`
- `AnsiString` (used in windows only)
- `Utf16String` (used in windows only)
- `Int`
- `UInt`
- `Long`
- `ULong`
- `Short`
- `UShort`
- `Float`
- `Double`
- `S8/S16/S32/S64` - signed 8/16/32/64 bit integer
- `U8/U16/U32/U64` - unsigned 8/16/32/64 bit integer
### File IO
- `File.writeAllText(path, text);`
- `var text = File.readAllText(path);`
## CLI
The main command is `frida`, which allows for most interactions (like loading a script)
### Attachment
Run binary and attach: `-f <file>`.
You can add arguments in the end (and therefore run any shell command).
If any argument starts with `-` then put `--` beforehand.
Attach to process by name: `-n <name>`
Attach to process by PID: `-p <PID>`
### Loading a script
Used on the `frida` command.
Add `-l <script-path>`.
### Other arguments
`--stdio=inherit|pipe` - inherit stdio of the application (by default) or allow piping it.
`--pause` - pause the script immediately, resumes when `%resume` is executed.
`-c <script name>` - load instrumentation script hosted in https://codeshare.frida.re/browse (contains a lot of existing scripts, can search using https://konsumer.js.org/frida-codeshare/#)
### frida-trace
Allows you to see function calls, and allow basic executing of logic when a function is called.
Works for system API calls or libc calls.
Usage: `frida-trace <attachment> -i "<method_pattern>"`.
Pattern can use `*` as wildcard.
You can specify `-i` twice to attach multiple handlers.
Will log when enters a method that matches the pattern, and create a handler for it you can modify.
Will sometime create 2 handlers for 2 DLLs for the method, you can modify only one if you want.
The handler is of this format:
```js
{
	onEnter: function(log, args, state) {
	
	},
	onLeave: function(log, retval, state) {
	
	}
}
```
You can use `log(str)` to log a string. `args` is an array of native pointers and `retval` is a native pointer.
You can use them as in [[#Native Pointers]], and read / edit them.
## Python API
Used for the control script - loading the instrumentation script, injecting it and communicating with it.
### Running a file
```python
pid = frida.spawn(["file"])
```
You can add parameters (and therefore execute any shell command) by putting them as additional elements in the list.
### Attaching

### Injecting script

## On Android
TODO write how to inject scripts and similar on android.
