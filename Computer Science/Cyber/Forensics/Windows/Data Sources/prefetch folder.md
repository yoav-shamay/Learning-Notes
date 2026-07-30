In `C:\Windows\prefetch`
Can have paths of run executables and some more data like executed time.
Can be parsed using `pecmd` from Eric Zimmerman tools.
Does not work with wine.
The usage is `PECmd.exe -d <prefetch dir> --json <out file name>`
In addition, generally (unsure, TODO verify):
- The creation time of the file is the first execution time + about 10 seconds.
- The modify time of the file is the last execution time + about 10 seconds
- Might want to try subtracting various amounts, can be closer (maybe the same).