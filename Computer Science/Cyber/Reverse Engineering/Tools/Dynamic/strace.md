`strace` shows all system calls done in a binary.
Can grant a good look on the functionality of the program.
Usage `strace ./<binary>`.
Useful Flags:
- `-s N` - max string size to print, can be useful if you want to export a string, can set to a very large number (like `10000000`) for infinity.
- `-e <call>` - filter to only this call.
- `-o out` - output to a file.
- `-xx` - print strings as raw hex, not interpreted ASCII (as `\xXY`)