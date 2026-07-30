## Connecting
### Using File Explorer
Connect to `smb://ip:port` in file explorer (omit `:port` if obvious)
### Using `smbclient` command
Listing shares: `smbclient -L ip`
Connecting to share: `smbclient \\\\ip\\sharename`
Add `-p port` to specify port
You can navigate using `ls` and `cd`
Downloading file: `get filename`