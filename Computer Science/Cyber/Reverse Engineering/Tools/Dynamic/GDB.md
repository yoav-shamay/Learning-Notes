## pwndbg cheatsheet
https://pwndbg.re/CheatSheet.pdf
## Running binary
- `run` - run without extra breakpoint
- `run arg1 < in_file > out_file` - acts like a binary execution in terminal in terms of arguments and redirections
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
`set $rsi = "123456789000"` - automatically allocates a string (using `malloc`) and puts a pointer
## Stepping and Continuing
- `si` - step single instruction, going into calls, like Step Into.
- `ni` - step single instruction without going into `call`.
- `continue` (or `c`) - continue until hitting a breakpoint (or program ends).
- `finish` (or `fin`) - go to just after the current function finishes. Prints the return value of the function.
- `until` (or `u`) - Basically step that skips loops. Continue running until an instruction after this instruction (in the current function) is reached.
- `until <loc> / u <loc>` - steps until reaching `loc` or the current function returns. Will only trigger on location in the same stack frame. Basically like a tmeporary breakpoint at `loc` and continue, but will only work in the current function.
- `advance <loc>` - same as `until <loc>` but will work even if the location isn't in the current function (but will still stop when the current function returns)
## Modifying program flow
- `jump <loc>` - jumps to `loc` and continues
- `return / return <expression>` - returns from the current function, optionally setting `expression` as the return value (basically saves it in rax)
- `call (int)func_name(param1, param2, param3)` (`int` is the return type) - calls a function and continues
## Getting binary / libc base addresses
- Use `info proc mappings` to see maps of libc / process. Base address can be determined from it
## Assigning variables
Useful for assigning a variable for usage in expressions, such as binary base address.
`set $var = value`
## Catching Syscalls
- `catch syscall` (all syscalls)
- `catch syscall openat` (one syscall)
- `catch syscall 0` (by number)
- `catch syscall read write` (multiple types)
Will stop twice for every syscall - one time immediately before its execution (allows to edit parameters) and one immediately after (allows to edit return value)

The syscall number is in `orig_rax`.

In order to cancel the syscall, change the number to `-1` (invalid syscall number, this will change rax to -38 (-ENOSYS) but do nothing)

You can change the return value after the syscall runs in `rax`.
## Watchpoint
`watch <expression>`
Watching at address: `watch *(int *)(0xaddress)`
If you do `watch -l *(int *)($rbp - 0x24)` it will evaluate it once and always watch the evaluated address, which can be useful to use register's current values in the expression.