The idea is that a docker container kernel is shared with the host system.
Docker containers usually have limited capabilities, even as root.
But if you have enough capabilities, you can get RCE on the host system
If you have `CAP_SYS_ADMIN` or `CAP_PTRACE`, you can most likely escape.
See [[Capabilities]] for more information.
## Detecting docker environment
- `.dockerenv` file in root
- `ps aux` - check first process
- `hostname` - random hash on docker
## Mounting host filesystem
See [[Using disk image file]]. can write or mount.
Note that the kernel is shared with the host, and also the filesystems, so it works.
If you have the right capabilities (TODO what) it will work.
## Tips
- Run `mount` to see links from host machine to this machine.