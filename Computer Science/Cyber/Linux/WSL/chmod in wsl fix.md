chmod won't work in wsl without the following:
edit `/etc/wsl.conf` and add the following to the end
```
[automount]
options = "metadata"
```
now run `wsl --shutdown` in powershell and restart wsl (or restart the computer)