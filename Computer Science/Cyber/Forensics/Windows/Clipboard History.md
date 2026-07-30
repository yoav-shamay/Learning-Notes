## See if it's enabled
See registry entry `HKCU\SOFTWARE\Microsoft\Clipboard`, entry `EnableClipboardHistory`. if it's 1 then it's enabled, if it's zero then it's disabled
## Using `ActivitiesCache.db`
see [[ActivitiesCache.db]]
See rows where `ClipboardPayload` is not `NULL`.
## Other paths to try (untested)
- `C:\Users\<Username>\AppData\Local\Microsoft\Windows\Clipboard`
- 