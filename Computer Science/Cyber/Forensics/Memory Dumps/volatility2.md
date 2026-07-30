Used to analyze memory dumps.
Has lots of plugins, each of them does different things
Usage: `volatility -f <file> --profile=<profile> plugin`.
In arch use `vol.py` instead.
First: [[#Determining profile|determine the profile]], needed to use any plugin,
Doesn't work for windows 10+
## Determining profile
Best option: run the `imageinfo` plugin, will give you it directly.
Might be too slow though.
In this case, volatility3 `windows.info` plugin can give you the profile.
To match:
https://github.com/volatilityfoundation/volatility/wiki/2.6-win-profiles
- Windows 7 - appears as 6.1 in volatility3 - `Win7SP1x64` (or `x86` for 32 bit)
- Windows 10 - appears as 10.0 in volatility3 - `Win10x64` (or `x86` for 32 bit) - doesn't work for most builds.
TODO finish
## Plugin list
- Getting running processes: `pslist`
- CMD run commands: `cmdscan`
- CMD interactions (including commands and stdin / stdout, full view of the terminal): `consoles`
- Environment variables: `envars`
- Clipboard: `clipboard`. add `-v` to show binary data in hex
- NTLM hash (user password hashes): `hashdump`
- notepad text: `notepad`
- Internet explorer history `iehistory`
- Show hidden processes: `psxview`
- Getting file list: `filescan`
- Extraction file: `dumpfiles -Q offset --dump-dir out_dir`
- Dump process memory: `memdump -p PID --dump-dir out_dir`
- Convert to `windbg` `.dmp` format: `raw2dmp` (TODO specific process? didn't try)
## Installing plugins
Put in the plugins directory, in `/usr/lib/python2.7/site-packages/volatility/`
## Different output format
Add `--output=<format>`, for example `--output=json`
Available formats:
- `text` - normal
- `dot` - graphviz dot diagrams
- `html` - html
- `json` - json
- `sqlite` - sqlite3 database
- `quick` - Faster version of text, but pipe separated values (untested, unsure what means)
- `xlsx` - excel spreadsheet (`.xlsx`)