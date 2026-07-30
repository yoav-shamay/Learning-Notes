GID is pretty much equivalent.
https://0xdf.gitlab.io/2022/05/31/setuid-rabbithole.html
## RUID, EUID, SUID
In Linux, each process has 3 UIDs: real UID (sometimes referred as just UID), effective UID and saved UID.
At any point, each of the RUID, EUID, SUID can be changed to any of RUID, EUID, SUID.
RUID is the the ID of the user who started the process.
EUID is also usually the ID of the user who started the process, unless on `setuid` binaries. On `setuid` binaries it's equal to the owner of the file.
SUID usually equals RUID, it's for when a privileged process wants to drop privileges and return to the previous ones later.
File and other permission checks are almost always based on `EUID`.
However, when spawning a shell (I think only bash, but `/bin/sh` also typically symlinks to it), normally if RUID != EUID, EUID is set to RUID.
On `setuid` binaries, it will drop the privileges again.
This can be disabled with the `-p` command line argument.
It can be sent using `execve` in case `argv` is controlled.
With `system` it's impossible.
## `execve` and `system`
When calling `execve`, `ruid` and `euid` are unchanged. `suid` is set to `euid`.
`system` is just a wrapper to `fork`, and `execl("/bin/sh", "sh", -c", cmd, (char *)NULL)`.
This means `system("/bin/sh")` is `/bin/sh -c /bin/sh`.
However, note that without `-p`, `/bin/sh` will set EUID to RUID.
And with `system` you can't pass this argument, as it will pass the second shell.
## Changing UIDs
The `setuid` system call, unlike what you might expect, if the process doesn't have root privileges (`euid` of root), will only change the `euid` to the input UID (if it's one of RUID,EUID,SUID).
If the process has root privileges, `setuid` will set all of them.
If you want to change RUID separately, you should use the `setresuid(newruid,neweuid,newsuid)` or `setreuid(newruid,neweuid)` (res = r,e,s, re = r,e)