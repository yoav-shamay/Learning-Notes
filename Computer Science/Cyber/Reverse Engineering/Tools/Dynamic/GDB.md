## pwndbg cheatsheet
https://pwndbg.re/CheatSheet.pdf
## Running binary
- `run` - run without extra breakpoint
- `starti` - start and break immediately on entry.
## Setting Breakpoint
`break <loc>` - set breakpoint at `loc`
## Deleting Breakpoints
- `info break` - list breakpoints and their number
- `del <num>` - delete breakpoint numbered `num`
## Specifying location
`break method_name`
`break *0x1234`
`break *(method_name + offset)`
## Getting values
show directly: `print` or `p`
get at the address `x`
To reference register add `$` before its name like `$rbp`
### Format Specifiers
Note that `p` doesn't support size specification, only format
`x/xg address` - hex, 8 byte
`x/sb` - string
`x/4xb`  - hex, bytes, 4 subsequent
## Viewing stack return address
use the `info frame` command to see where rip is saved (and what's rbp is)
## Jumping to a location
## Setting Values
`set varname = 1`
`set {int}0xaddress = 1`
## Stepping and Continuing
- `si` - step single instruction, going into calls, like Step Into.
- `ni` - step single instruction without going into `call`.
- `continue` (or `c`) - continue until hitting a breakpoint (or program ends).
- `finish` (or `fin`) - go to just after the current function finishes. Prints the return value of the function.
- `until` (or `u`) - Basically step that skips loops. Continue running until an instruction after this instruction (in the current function) is reached.
- `until <loc> / u <loc>` - steps until reaching `loc` or the current function returns. Will only trigger on location in the same stack frame. Basically like a tmeporary breakpoint at `loc` and continue, but will only work in the current function.
- `advance <loc>` - same as `until <loc>` but will work even if the location isn't in the current function (but will still stop when the current function returns)
## Modifying program flow
- `jump <loc>` - jumps to `loc`
- `return / return <expression>` - returns from the current function, optionally setting `expression` as the return value (basically saves it in rax)
## Getting binary / libc base addresses
- Use `info proc mappings` to see maps of libc / process. Base address can be determined from it
## Assigning variables
Useful for assigning a variable for usage in expressions, such as binary base address.
`set $var = value`