## General tips
- `obj.xyz` can be replaced with `obj['xyz']`. Any global can be accessed using `window['xyz']`
- You can override object `toString` to call a function automatically when parsing it as a string, and do it in another way.
- You can access the `Function` constructor using the `constructor` attribute of any function, for example `alert['constructor']`. You can use this to get eval: `alert["constructor"]("alert(1)")()`
- You can get a function using a function property of other object, for example `[]["filter"]` is a function or `[]["constructor"]`.
- You can write any code using `[]()+!`, a converter is in https://jsfuck.com/. Has also a good cheat sheet in the bottom.
## Getting Chars
- `\xHEX`
- `\oct`
- `('' + object)[index]` (or slicing) - get the char at `index` from the name of `object`
- `String.fromCharCode(code)`
- `atob("base64")
### Getting certain objects
Can be used with the `('' + object)` trick
- `[][[]] = undefined`
- `+[] = 0`
- `+!+[] = 1`
- `!+[]+!+[] = 2`
- `![] = false`
- `!![] = true`
- `+[![]] = NaN`
- `+(+!+[]+(!+[]+[])[!+[]+!+[]+!+[]]+[+!+[]]+[+[]]+[+[]]+[+[]]) = Infinity`
- `[]['filter']` (or any other function) when converted to string generates: `"function filter() { [native code] }"`
## Getting `window`
- `window`
- `self`
- `[]["filter"]["constructor"]("return this")()` (`"filter"` is just an example function)`
## Calling a function
The general goal is to call `eval` or something similar
- https://portswigger.net/research/the-seventh-way-to-call-a-javascript-function-without-parentheses contains some hacks
- You can call function by using \`\` instead of `( )`. the first parameter will be an array splitted by `${}`, the second parameter will be the first `${}`, third one the second `${}` and so on.
- Function with no parameters can be called with \`\` like `()` normally
-  ``function.call`${smth}` `` - puts `smth` as argument directly.
- `a instanceof b` calls `b[Symbol.hasInstance](a)` if `b` has this method. You can create an object with custom `Symbol.hasInstance` to use this to execute any method, for example: `'code' instanceof {[Symbol.hasInstance]: eval}`.
- `"" + {"toString": x=>alert(1)}`
## Executing code in string
- `eval("code")`
- `Function("code")()`
- `setTimeout("code", 1)`, also works with backticks - `` setTimeout`alert(1)` ``
## Other interesting features
- A square bracket in the name of a field in an object will evaluate the code inside it and the result (after conversion to string) will be the name of the attribute, for example `{["a" + "bc"]: "def}` is the same as `{abc: "def"}` or `{"abc": "def"}`
- Object keys in JS can be either String or Symbol.
- A symbol is a unique and immutable value, each call to symbol creates a unique value. JS has some builtin symbols like `Symbol.hasInstance`
- If `a` is an array then `[...a]` is the same as `a`
- If `a` is a string then `[...a]` is the list of the characters of `a` 
- `tagName` returns upper case when it's a normal HTML tag, but returns lowercase inside `svg` tag.
- You can define a variable after its used to prevent errors, at least with `var` (untested for `let`).
## Semicolons
https://en.wikibooks.org/wiki/JavaScript/Automatic_semicolon_insertion
Javascript has automatic semicolon insertion, in the following scenarios:
- Before newline
- TODO finish