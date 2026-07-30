## Range Specifiers
- `%` - all lines
## Global Command
`:g/pattern/command`
Run `command` on every line that matches `pattern`.
## vglobal command
`:v/pattern/command`
Inverse of `global` - run `command` on every line that doesn't match `pattern`
## Substitute command
`:[range]s/pattern/string` - replace pattern with string.
line range specified in `[range]`, current line if unspecified
## Delete command
`:[range]d`
line range specified in `[range]`, current line if unspecified