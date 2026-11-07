## Accessing
### Using GDB
Preferred method.
Run `gdb -q -batch -x <python file> <binary file>`

In the python file, use `import gdb` and access the API using the `gdb` module.

Use inside `run > output_file < input_file` to give a constant stdin to the binary, and access the stdout of the binary from the program.

You can run the binary file multiple times in the python program, using `run` or similar methods to start, and `stop` to stop it (or `continue` until it finishes execution).
### Using pwntools
```python
p = process("./exe")
_, debugger = gdb.attach(p, api=True)

p = gdb.debug(["./exe"], api=True)
debugger = p.gdb
```
Use `debugger` to access the API (instead of the normal GDB)
The main pro is easy stdin / stdout dynamic feeding, including while GDB is waiting for a breakpoint.
Sometimes does problems, and much slower, so when this isn't needed, using GDB API is preferred.
Using this execution method, running `debugger.execute("continue")` and similar runs does not wait until the binary hits a breakpoint.
To offset it you can use those methods:
- `debugger.wait()` - wait until reaching a breakpoint
- `debugger.continue_and_wait()` - equivalent to running continue and then wait
## Methods
- `gdb.execute("cmd")` - execute command.
- `output = gdb.execute("cmd", to_string=True)` - return output of command as string without printing it to terminal
- `res = gdb.parse_and_eval("$rbp")` - evaluate an expression
## Reading and Writing in memory
```python
inf = gdb.selected_inferior() # Can run once after initialization
content = inf.read_memory(0xaddress, length).tobytes()
inf.write_memory(0xaddress, b"content")
```
