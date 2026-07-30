## With `ps`
`ps aux` - all
`ps` - just my processes and some of them
## With `/proc`
First, you can see all `pid` and their owners with `ls -la /proc`.
You can get details about a specific `pid` (even without being its owner), you can use `cat /proc/pid/cmdline`
