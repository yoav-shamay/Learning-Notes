Topic called Memory Forensics.
Useful tools are volatility and memprocfs.
Prefer using volatility3 in case possible in both 2 and 3.
volatility3 plugins are denoted here as `windows.` while volatility2 are without prefix.
Note that volatility2 doesn't work for windows 10+.
https://book.hacktricks.wiki/en/generic-methodologies-and-resources/basic-forensic-methodology/memory-dump-analysis/volatility-cheatsheet.html - cheatsheet
TODO add memprocfs stuff, only volatility for now
TODO might want to split this
## General Useful Stuff to Check - windows
Useful to gather general information about what's happening.
By order of importance, though use common sense.
Volatility2 doesn't work for windows 10+.
- `windows.pslist`
- `windows.filescan`
- `windows.cmdline`
- `windows.cmdscan` / `cmdscan`
- `consoles`
- `windows.psxview` / `psxview`
- `windows.envars`
- `windows.handles`
- `clipboard`
- TODO memprocfs stuff
## General Useful Stuff to Check - Linux
- `linux.pslist`
- `linux.bash`
- `linux.psaux`
- `foremost <file>` - as an alternative to filescan
## Tips
- Redirect outputs to a file to prevent rerunning as it's slow
- First, see running processes and check every single one for important ones
- To see which file `notepad` and probably other programs opened (if opened like this on startup), look at their `cmdline`
- If I need a behavior try to google perhaps its a plugin I can download / exists
## Filtering relevant files
Specific things to filter (`grep`) in the `windows.filescan` output
Make sure to use `grep -i`
Look one-by-one if not too many (less than 50 is probably not too many)
- Desktop
- Documents
- Downloads
- User directory, and probably worth looking carefully one-by-one
- Filter by program name search for important files
- Windows event logs (`*.evtx`)
- Google 
- Ask an AI to filter the list
- Check files related to installed programs (examples: password manager -> vault file, browser -> history file, WinRar -> rar files), specifically filter by name / location / extension
- Search for keywords like `password`, `pass`, `flag`
## Using process memory dump
Dump entire process memory using `windows.memmap --pid pid --dump`
- `strings` and see highlights, stop quickly.
- `foremost -i dumpfile -o carved_files`
- `grep` flag format
- `grep` formats specific to program, like URLs in browser or SQLite databases
### Extracting file using signature manually
An open file is usually saved in the memory dump. 
For types binwalk / foremost doesn't support.
Write a python script that checks every sequence for the signature and extracts the content starting from them.
You can usually just take a big enough constant length, like `0x10000`, as if the length is longer than the actual file it usually doesn't cause problems when opening it.
## Browsers
- grep process memory for URLs
- `<name>history` plugin
- Can also see history by finding history file which is a sqlite3 database.
## Getting registry entries
First, get all hives using `windows.registry.hivelist`
Then, you can get all subkeys of a hive using the `windows.registry.printkey --offset <hive_offset>`
You can then get subkeys from a specific path using `--key "<subkey_path>"`, nest using `\`
For example: `--key "ControlSet001\Control\ComputerName\ComputerName"`
You can also just recursively get all subkeys of a path using `--recurse`
## Getting Specific Info
### Computer name (hostname)
Option 1: environment variable named HOSTNAME (grep it from envars)
Option 2: in registry (see [[Common Registry Entries]])
## Investigating a process
- see environment variables
- see open file handles
- extract process memory.