## With autoruns
If you can run the computer, [[Autoruns]] is the best tool.
## Persistence by Registry entries
Persistence keys can appear in:
Syntax `<a | b>` - either `a` or `b`
Standard:
- `<HKLM | HKCU>\Software\Microsoft\Windows\CurrentVersion\<Run | RunOnce>`
- `HKLM\Software\WOW6432Node\Microsoft\Windows\CurrentVersion\<Run | RunOnce | RunServices>`
- `HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\Explorer\Run\*
Rare overrides of existing autoruns (untested):
- `<HKLM | HKCU>\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon`, `Shell` / `Userinit` values
- `<HKLM | HKCU>\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Windows`, `AppInit_DLLs` value
- `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Windows`, `AppInit_DLLs` value.
- `<HKCU>\Environment`, `UserInitMprLogonScript` value
- `<HKLM | HKCU>\Software\Microsoft\Windows\CurrentVersion\Explorer\<Shell Folders | User Shell Folders>` - controls the paths of standard directories which can be used for persistence (like `Startup`)
## Task Scheduler
- using the `Task Scheduler` app
- Save location - `C:\Windows\System32\Tasks`.
### Using registry
Cached tasks can also be detected using registry entries from `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache`
The `Tree` folder corresponds to a tree like in the app, but the other directories can be used to see full info.
## Using Processes-run-at-startup history
See [[Process Run History]].
## Startup Folder
Check `C:\Users\<username>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\`