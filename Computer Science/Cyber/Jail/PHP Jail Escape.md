Use https://onlinephp.io/ to test on different PHP versions.
## Case Sensitivity
- PHP function names AREN'T CASE SENSITIVE.
- Variable names are case sensitive.
## Using include / require
Can use either `include file` or `require file`.
Can include remote files - `http://url`. Will run the code there, leading to an easy win.
## Primitives
### RCE
- `exec("cmd")` - runs `cmd` and returns stdout
- `` `cmd` `` - runs `cmd` and returns stdout
- `shell_exec("cmd")` - runs `cmd` and returns stdout
- `passthru("cmd")` - runs `cmd` and prints stdout
- `popen("cmd","w"/"r")` - will run `cmd`. if specified `w`, will return a file handle that prints to command stdin and will output whatever the command prints. If specified `r`, will instead return a file handle of reading from command stdin. stderr will be printed anyway.
- `system("cmd")` - runs `cmd` and prints stdout
- `proc_open` - TODO
### Getting files in directory
- `glob("pattern")` - returns an array of file names matching the pattern. Not full RCE but `ls`. pattern can use wildcards like `*` or `?`
- `scandir('directory_name')` (like `scandir('.')`) - returns an array of all files in the directory.
- `new finfo(0, '/')` - PRINT THE CONTENT OF ALL FILES in directory `/`. Will print it in a weird error message way, but includes all contents.
### Reading file
- `new finfo(0, '/')` - PRINT THE CONTENT OF ALL FILES in directory `/`. Will print it in a weird error message way, but includes all contents.
- `highlight_file("file_name")` - prints file content
- `show_source` - alias of `highlight_file`
- `file_get_contents("file_name")` - returns file content
- `read_file("file_name")` - prints file content
- `include("file_name")` - includes file, if it's plain text will just evaluate it as HTML and print its content
- `require("file_name")` - see `include`
- `gzfile("file_name")` - returns the content of file as an array of lines.
- `file("file_name")` - returns an array of the lines of the file
## Running code from string
- `eval('php_code');`
- `assert('php_code');`
- `unserialize('serialized_var')` - creates a class.
- `preg_replace` with `/e` TODO
- `RegexIterator` with `/e` TODO
## Using strings from request
- `$_GET` - url parameters
- `$_POST` - form data
- `$_COOKIE` - cookies
- `$_REQUEST` - union of `$_GET`, `$_POST`, `$_COOKIE`
Access:
- `$_GET["name"]`
- `$_GET[12]` also works if the URL parameter name is `12`
## Getting variable from string name
- `${'name'}` is equivalent for `$name`, inside the `{}` it's evaluated as an expression, can even be used inside (double quotes / heredoc) strings.
- `$$name` is equivalent to `${$name}`
## Strings
- You can concat strings using `.`, like `"a" . "b"`
- Single quotes string - can't escape anything but `\\` and `\'`, and doesn't substitute variables.
- You can escape in (double quote / heredoc) strings using `\xHEX` or `\OCT`
- php automatically converts unknown constants to strings, like `$s=string;` if there's no constant named string is equivalent to `$s="string";`. Will produce a warning, can surpass using `@`.
- This can be used with `~` if the string contains non-characters (like `~smth` where `smth` is the negation of `1*2`).
### String creation functions
- `chr(num)` - returns the character with ascii code num
- `hex2bin(hex_str)` - decodes hex string.
Some base conversion functions to help:
- `dechex(num)` - num to hex string
- `base_convert(num_str, from_base, to_base)` - convert `num_str` between  bases
- `bin2hex()` - converts ascii string to hex string

- `base64_decode(b64str)` - decodes base64 string
- `join(deilimiter, arr)` - string join.
- `implode(delimiter, arr)` - like `join`
- `str_increment(s)` - returns `s++` (increment last character)
- `str_rot13(s)` - returns rot13 of s
- `stripcslashes(s)` - parses backslashes including `\oct` or `\xHEX`.
More functions: https://www.php.net/manual/en/ref.strings.php
### Substitution in strings
Doesn't happen in single quotes / nowdoc
- You can put `$var` in the middle of a string expression - will be replaced by the value of `$var`.
- Allows for concat, like `"abc$var1$var2"`
- You can put `{var}` for advanced variable access - still has to be variable but can involve parameter access and more, like `"{$arr['foo'][2]}"`.
- You can also use `${var_name_expr}` and sometimes `${advanced_var}`
### Operators in strings
- You can `++` or `--` a string to modify its last character. `$a='abc';$a++;` - now `$a` contains `'abd'`. Note that `+=` doesn't work.
- Bitwise operators work on ascii code of each character: `~'a'`, `'a' | 'b'`, `'a' & 'b'`
- In the case of `'a' | 'ab'` (or for `&`), will only apply up to the length of the shorter string
- PHP can contain non-ascii characters inside strings like normal, even in the source itself in quotes, works well with negation. They are also parsed as string when used without quotes.
### Heredoc and nowdoc strings
Multiline strings, doesn't use quotes.
Heredoc:
```php
$a = <<<END
asdasd
asdasdasd
END;
```
END can be substituted with anything.
Work the same as double quote string.
Pretty strict about the boundary but allows some flexibility.
See https://www.php.net/manual/en/language.types.string.php for full details
Nowdoc strings:
```php
$a = <<<'END'
something
\\
\'
END
```
The single quote analog to heredoc. All backslashes are taken literally, no escaping.
## Calling a function
- `name(params)` - standard
- `$a = "name"; $a()`
- `"name"()` - from PHP 7
- `('ex'.'ec')('ls');` - from PHP  7
- `param |> func` - equivalent to `func(param)` - from PHP 8.5
- `echo`, `print`, `include`, `require`, `include_once`, `require_once`, `die`, `exit` don't require parenthesis.
- `use function name as alias; alias("param");` - from PHP 5.6. the `use` must be in global context (not inside a function)
- You can pass more parameters to a function then it needs, they will be ignored.
### Using `CallbackFilterIterator`
`CallbackFilterIterator` allows filtering an iterator based on a callback.
When iterating on a `CallbackFilterIterator` it will call `callback(value, index, iterator)` and if it returns true, it will keep this value.
```php
function fun1()
{
	yield 1;
	return;
}
$a = fun1(); // create an iterator

$b = new CallbackFilterIterator($a, "fun_name");
foreach ($b as $c)
{
	continue;
}
```
Internally calls `fun_name(1, 0, $a)`.
You can use this to alias `CallbackFilterIterator`:
```php
class alias extends CallbackFilterIterator implements Iterator {}
```
and use `alias` instead of `CallbackFilterIterator`
## Omitting spaces
- there doesn't need to be a space between keywords and variable names. `echo$v;`
- In general if a space appears unnecessary it's probably unnecessary.
## Array access
normal:
- `$a[index]`
- `$a{index}` - prior to PHP 8
unpacking:
- `list($a, $b, ...$rest) = $arr`
- `list($a, $b) = $arr` (`$a` - first element, `$b` - second element)
or equivalently, from php 7 - 
- `[$a, $b, ...$rest] = $arr`
- `[$a, $b] = $arr` 
also supports nested arrays:
- `[[$a]] = [[1,2],3]`
- `list(list($a)) = [[1, 2], 3]`
Can also just use commas instead of unnecessary variables:
- `list(,$a) = [1, 2]`
- `[,$a]=[1,2]`
Argument unpacking:
- `func(...$arr);` - puts all values of `$arr` as arguments;
keyed unpacking:
- `['a' => $val] = ['a' => 'b']`
Foreach loop:
- `foreach($arr as $val) {}`
- `foreach($arr as $key => $value) {}`
## Predefined variables
Variables defined in every code
https://www.php.net/manual/en/reserved.variables.php
## Creating an instance of class
- `new` can be used without parenthesis: `$obj = new Class;
- `$a = "Class"; new $a;
- `$arr = ["Test"]; new $arr[0];`
## Accessing private property of class
- https://dev.to/goodevilgenius/accessing-private-properties-in-php-without-reflection-95m
### Using reflection
- https://stackoverflow.com/questions/11604946/can-i-get-the-value-of-a-private-property-with-reflection
```php
$instance = Class();

$p = new ReflectionProperty($instance, 'x');
$p = new ReflectionProperty('className', 'x');
$r = new ReflectionObject($instance);
$r = new ReflectionObject('className');
$p = $r->getProperty('x');

$p->setAccessible(true); // not neccessary from PHP 8.1
$val = $p->getValue($instance);
$p->setValue($instance, 5);
```
### Using session
If the page uses session, you can save an instance of a class where the variables has the correct values, then access it in another time.
This will only work if the class has the same name.
TODO namespaces for redecleration? https://stackoverflow.com/questions/2658906/is-there-any-way-to-redeclare-a-class-safely-in-php
## Useful Features
- You can call a class and a function by the same name and it won't interfere.