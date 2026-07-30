Used to analyze memory dumps.
Has lots of plugins, each of them does different things
Usage: `vol -f <file> <plugin-name>`
## Downloading symbols for linux
`linux.pslist` might not work right away, and might require downloading symbols.
Can do it automatically using `vol --remote-isf-url 'https://github.com/Abyss-W4tcher/volatility3-symbols/raw/master/banners/banners.json' -f <memory_dump> <plugin>`. Only need to do once, later can use `vol` normally.
### Manual installation
Couldn't get to work, so probably wrong somewhere.
Running `banners.Banners` will detect OS and version.
This repository has symbols for almost all Linux and macOS versions: https://github.com/Abyss-W4tcher/volatility3-symbols/
Note that the version is based on the kernel version (such as `Linux version 5.4.0-1059-azure`, not GCC version (even if it shows like `Ubuntu 7.5.0-3ubuntu1~18.04`)). Also it's most likely `amd64`.
You can also use https://raw.githubusercontent.com/Abyss-W4tcher/volatility3-symbols/refs/heads/master/banners/banners_plain.json for quick mapping of banner -> symbol path.
Place the compressed symbol file under `<volatility 3 installation>/symbols/linux` (create if doesn't exist).
Installation directory in arch is `/home/yoav_s/.local/lib/python3.12/site-packages/volatility3`
## Setting output format
Use `-r <format>` in the beginning
`vol -r json -f <file> <plugin-name>`
Available formats:
- `json`
- `csv`
- TODO finish
## Plugin List
### Windows
- General info: `windows.info`
- See running processes: `windows.pslist`
- Dump entire process memory as one file: `windows.memmap --pid <PID> --dump`
- Extract file at specific offset: `windows.dumpfiles` with `--physaddr <offset>` (Try `--virtaddr <offset>` if it doesn't work)
- List files: `windows.filescan`, shows physical address of each file for extraction (if I want to find a specific file), redirect to file as large and slow.
- Get process hierarchy: `windows.pstree` (to find main process in case of multiple)
- View active cmdlines and their startup commands: `windows.cmdline`, basically information about startup of a bunch of processes like a file they were opened on
- cmd run commands: `windows.cmdscan`
- View environment variables: `windows.envars`
- user password hashes (NTLM hashes): `windows.hashdump`
- See all open handles (like file handles): `windows.handles`, allows to see open files
- See open network connections (and related process): `windows.netscan`, `windows.netstat`. `netstat` is faster but might miss hidden connections.
- Strings: `windows.strings`, can filter by PID, requires `--strings-file` that will search strings only from this file
- Show hidden processes: `windows.psxview`
- Alternatives to `pslist` (untested): `windows.psscan`, 
- Get all registry hives: `windows.registry.hivelist`
- Get registry entries from hive: `windows.registry.printkey --offset <offset> --key <path>`
- Getting VADs: `windows.vadinfo --pid <pid> [--dump]` - output all VADs, `--dump` actually dumps them as file. Specify `-o dir` in the beginning to output in another directory.
### Linux
- Active processes - `linux.pslist`
- Bash history - `linux.bash`
- Show processes cmdline: `linux.psaux`
- Alternative to `pslist` that can show hidden processes: `linux.psscan` (untested)
- Showing active IP connections - `linux.ip.Addr` and `linux.ip.Link` (unsure of differences)
- Show open files for each process - `linux.lsof`
- Show environment variables for each process - `linux.envars`
- List `/proc/<pid>/maps` for each process - `linux.proc.Maps`
## Installing plugins
Place script at `python_path/site-packages/volatility3/plugins/<windows | linux>`