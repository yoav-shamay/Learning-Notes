https://regseek.github.io/ - cheat sheet
- Computer Name - `ControlSet001\Control\ComputerName\ComputerName` in `\REGISTRY\MACHINE\SYSTEM` hive
- Default Browser - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\Shell\Associations\URLAssociations\(http|https)\UserChoice`. This has the ProgID.
- Recovery Question Answers - `HKLM\SAM\Domains\Account\Users\<USERID>`, `ResetData` entry - `UTF-16LE` json.