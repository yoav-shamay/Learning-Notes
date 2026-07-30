To bypass syscall restrictions.
TODO extend.
## File access
### Opening a file
- `open` - standard
- `openat`
- `name_to_handle_at`, `open_by_handle_at`
### Reading from an open file
- `read` - standard
- `mmap` (by mapping from file)
### Not requiring open
- `chmod` - can allow a user to open it
- `chown` - can allow a user to open it 
## Getting full RCE
### Spawning a shell
- `execve` - can execute a file in the current process, like `/bin/sh`
### Low syscall alternatives
- `chmod` - can make `/etc/passwd` writable, allowing full PE from another shell in a single syscall. Alternatively you can make `/bin/sh` setuid