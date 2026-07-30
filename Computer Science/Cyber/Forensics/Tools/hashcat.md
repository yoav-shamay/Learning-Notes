A tool that allows you to brute force a password from hash.
Can be used in combination with john the ripper in order to get the hash from a zip or another file.
Usage: `hashcat -a 0 -m <mode> <hash file> /path/to/rockyou.txt`.
Can also use on windows but make sure to specify absolute path of hash file.
If you do not specify `-m <mode>`, it will attempt to auto detect the mode.
Useful if you don't know it, though if you know the source it might be better to figure out yourself.
## Common Modes
- md5 + salt: `20` (format: `hash:salt`, salt can be empty)
- bitlocker user password: `22100`
- winzip: `13600`
- `pkzip`, single file:  `17200`
- `pkzip`, alternative: `17210`
- `pkzip`, multiple files: `17220`
- rar5: `13000`
- keepass: `13400`