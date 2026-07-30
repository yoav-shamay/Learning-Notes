## sudo Limitations
You can limit available commands a user can run in `sudo`.
This appears in `/etc/sudoers.d/username` (needs root to read/write)
You can use `sudo -l` to see available commands you can run as sudo without any other permissions.