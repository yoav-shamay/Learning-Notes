A security mechanism limiting syscalls that can be called by the program.
Can be used as an unbypassable sandbox.
Has 2 modes: `SECCOMP_SET_MODE_STRICT`, `SECCOMP_SET_MODE_FILTER`.
## Strict mode
Allows only `read`, `write`, `_exit`, `sigreturn`.
Will terminate the program in case of any other syscall.
Note that doesn't even allow editing files.
## Filter mode
Has a configurable filter of allowed syscalls.
In order to use this, the caller thread must have CAP_SYS_ADMIN (usually root, see [[Capabilities]] for more details), or the thread must have the `no_new_privs` bit set (which means this thread cannot gain additional privileges, for example using `execve` on a `setuid` program, this is to ensure you can't change behavior of setuid programs. TODO when this is set).
## Using limited syscalls
https://github.com/unixist/seccomp-bypass (untested)
- `chmod` - can give access to a file in a single syscall, `/etc/passwd` will allow for PE, or making `/bin/sh` setuid
- See [[Useful Syscalls]] for syscall options for common operations.