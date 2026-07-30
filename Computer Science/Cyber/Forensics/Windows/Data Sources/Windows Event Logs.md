Can be opened with windows event viewer.
Can also use [https://pypi.org/project/python-evtx/ ](https://github.com/williballenthin/python-evtx)- to automatically parse, also works in linux.
Logs are usually saved in `C:\Windows\System32\winevt\Logs`
## Useful categories
- Sysmon logs (`Microsoft-Windows-Sysmon Operational`) can be extremely useful, most of the time doesn't exist though (sysmon is a program that needs to be installed and activated for the logs to exist)
- Powershell logs (including run commands) might be saved in the folder as `Windows PowerShell.evtx`
- In `Security` logs you can see logs related to user login, logout, user and group creation / deletion / privileges changes
## General tips
- If in a VM might want to extract the files locally and open in my machine. 
- Try to look around the time something important happened.
## Finding logs
- You can use Find to filter by string
- You can use Filter to filter by event ID or user or something else.
- You can also filter by time in the `Filter` in the `logged` row.
## Other Resources
https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/appendix-l--events-to-monitor - all event ids