Reference: https://www.gnu.org/software/bash/manual/bash.html#Shell-Expansions. Also includes more details about each of the expansions.
Before shell expansions, the command is split into words. Some shell expansions might make one word expand into more than one word.
## Shell Expansion Order
1. Brace Expansion
2. Tilde Expansion
3. Shell Parameter Expansion
4. Command Substitution
5. Arithmetic Expansion
6. Process Substitution
7. Word Splitting
8. Filename Expansion
9. Quote Removal
## Brace Expansion
Appears when a word has brackets, will expand to all possibilities.
For example: `{a,b,c} -> a b c` or `{1..3} -> 1 2 3`, or `a{d,c,b}e -> ade ace abe`, or `{1..5..2} -> 1 3 5`.
## Tilde Expansion
In short: ~ to home directory.
Happens when first character in word is ~. tilde-prefix is all characters from ~ to the first unquoted slash, and it will be replaced.
If no characters in tilde prefix are quoted, it is treated as a login name.
If it's the null string it's replaced with $HOME or home directory of executing user if unset. 
Otherwise, it's replaced with the home directory of the user with this login name.
If the tilde prefix is ~+, it will be replaced with $PWD
If it's ~-, it'll be $OLDPWD (if set, otherwise won't be substituted)
If it's number N maybe preceded (+/-) (by default +), it'll be replaced with the corresponding element from the directory stack, the output of `dirs (+/-)N
## Shell Parmeter Expansion
In short: used to expand shell variables.
`parameter` can be:
- a name of an environment variable, will be expanded to its value
- `*` or `@` TODO
- `arr[index]` - array at specific index.
- `arr` - the first value of arr.
- `1`-`10`
Possible expansions:
- `${paramter}` / `$parameter` replaced with `parameter` (or nothing if it's unset)
- `${parameter-word}`  replaces with `parameter` or `word` if `parameter` is unset or null
- `${paramter:=word}` if `paramter` is unset or null, assigns `word` to `var`. Then it's substituted with the value of `var`.
- `${paramter:?word}` If `paramter` is unset or null, `word` is printed to stderr and the shell (if not interactive) exits. Otherwise substitutes with `var`.
- `${paramter:+word}` If `paramter` is unset or null, substituted with nothing. Otherwise substituted with `word`.
- `${!prefix*}`  / `${!prefix@}` names of variables that their name begins with prefix, separated by whitespace (first character of `$IFS`). If appears in double quotes and with `@` each variable expands to a separate word.
- `${!name[*]}` / `${!name[@]}` all keys in array called name, if it's an indexed array it's just 0,1,2,3,...,len-1. 0 if name is not an array. If in double quotes and `@` is used then each key will be a separate word.
- `${#parameter}` - the length in characters of  the expansion of `parameter`.
- `${#*}` / `${#@}` - the number of positional parameters
- `${#arr[*]}` / `${#arr[@]}` - the length of array `arr`.
- TODO finish
### Substring Expansion
`${parameter:offset}` or `${parameter:offset:length}`
Expands up to length characters (unbound without length) of the value of parameter starting at the character specified by offset.
Length and offset are arithmetic expressions.
Offset is 0 indexed.
If offset is negative, it's offset in characters from the end (-1 is last character, -2 the one before it, etc) (in all cases).
If parameter is @ or \*, the result is *length* positional parameters beginning at *offset*. If length is negative, it's an expansion error. A positional parameter is an argument to the shell (or program executing this). In this case (and only this one) *offset* is 1-indexed.
If parameter is an indexed array name with @ or \* in index after it, it takes *length* members of the array starting with index *offset*.
Example; `${array[@]:2:3}` - the next 3 elements in array starting from index 2 
Note that in the case of negative index you need space after the `:` so it won't be interpreted as the `:-` operator.

## Command Substitution
When $(command) or \`command\`
command is executed and it's replaced with the stdout of the command, with trailing newlines deleted.
Note: `$(cat file)` is equivalent to (and slower) than `$(< file)`

## Arithmetic Expansion
`$((expression))` is replaced with the evaluation of the arithmetic expression.
More details in https://www.gnu.org/software/bash/manual/bash.html#Shell-Arithmetic
## Process Substitution
`<(command)` - the output of command is saved in a (temporary) file and the expression is replaced with the file name. for example: `cat <(echo hey)` - will save the output of echo hey in a file and provide it as an input to cat.
`>(command)` - will be replaced with a filename that the command should write to. Then the file content is given as input for the command (I think stdin but unsure)
## Word Splitting
Scans the results of parameter expansion, command substitution and arithmetic expansion not in double quotes.
Splits those to words.
Each character of `$IFS` is treated as delimiter. Splits the other expansions into words using those characters (`$IFS` is probably `<space><tab><newline>`).
If `$IFS` is unset or contains some of `<space><tab><newline>` those characters as trailing or leading in expressions (words) are ignored (the ones it contains if not unset).
If `$IFS` is null no word splitting occurs.
Explicit null arguments ("" or '') are retained and passed as empty strings.
Implicit null arguments are removed (expansion of parameters with no value, unless expanded within double quotes).
When quoted null argument appears as part of word with non-null expansion, the null argument is removed (`-d'' -> -d`)
## Filename Expansion
Scans each word for \* , ? and \[.
If one of those appears unquoted then the word is regarded as a pattern, and replaced with alphabetically sorted list of filenames matching the pattern.
If there are no matches, depending on the shell options, the word will be left unchanged, removed, or there will be an error.
More details: https://www.gnu.org/software/bash/manual/bash.html#Pattern-Matching
## Quote Removal
All unquoted appearances of backslash, single or double quote that didn't result from one of the above expansions are removed.