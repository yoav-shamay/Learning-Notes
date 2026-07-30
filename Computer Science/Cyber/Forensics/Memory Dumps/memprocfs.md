A tool that allows mounting memory dumps to visualize them.
Usage: `memprocfs -device chall.raw -mount ~/memprocfs_mount`.
wiki - https://github.com/ufrisk/MemProcFS/wiki
## Accessing Process directory
Can access process by 2 ways:
- `/name/<name>`
- `/pid/<pid>`
Result is the same
## Enabling Forensic directory
Performs forensic analysis, needed to access stuff in `forensic` directory.
to enable, change `/forensic/forensic_enable.txt` to `1-4` (see `readme` for more details). Should use `4`, unsure of real difference.
Then wait, progress can be seen in `/forensic/progress_percent.txt`.
Will also print to console when done.
## Accessing files
In `forensic` directory.
2 directories - both the `file` and the `ntfs` (from `mft`) directories contain partial trees.
One might contain stuff that the other won't.
Both can contain file content but it might be corrupted.
`ntfs` usually generates more complete tree but less files might have content.
## Getting `dmp` format of process
Go to the `minidump` folder in the process directory, it appears as `minidump.dmp`.
