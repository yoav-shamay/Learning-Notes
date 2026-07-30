## File Path
- User registry (`HKEY_CURRENT_USER` / `HKEY_USERS\<sid>`) is saved in `C:\Users\username\NTUSER.DAT`
- System registry (`HKEY_LOCAL_MACHINE\<file name>`) is saved in `C:\Windows\System32\config\` (`<file name>` is the specific file in the directory).
## Opening
Can be opened using Eric Zimmerman Registry Explorer
https://ericzimmerman.github.io/#!index.md
Does not work with wine.
The `LOG1`, `LOG2` and similar files are transaction logs and can provide additional information, `Registry Explorer` will ask for them so might be worth providing (TODO details).