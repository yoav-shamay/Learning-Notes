The `/proc/<process id>` folder has a lot of info about the process, that can be read as files.
You can also refer to `/proc/self` for current process.
## `fd` Directory
In the `fd` folder there are symlinks to all files opened by the process.
The symlink name is a number that gets assigned sequentially (0,1,2,3,4,...).
`/dev/fd` is a symlink to `/proc/self/fd`.
### Potential usage
If a process opens the flag file (for example when another team reads it if it's the same instance, or just opens a file pointer but doesn't close), you can use this.
You can brute force the symlink name (small number)
You can see process name in docker if it's on startup, or brute force it given that PIDs are mostly sequential.
## Latest process id
You can also see the latest process id in `/proc/sys/kernel/ns_last_pid`.
Allows to guess a process id, as it's a good approximation and you can always brute force the difference.
## `exe` file
Points to the running executable, useful when you don't know its name.