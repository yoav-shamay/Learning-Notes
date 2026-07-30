See https://man7.org/linux/man-pages/man5/passwd.5.html
In each row, separated by colon:
- User name
- Password - `x` if saved in `/etc/shadow` (almost always in modern systems). can also contain a password hash directly. The hash format can be modern like `/etc/shadow` or older [[Traditional des crypt hash]]. Can also contain `*` to indicate that you can't login to this account with a password.
- UID
- GID
- GECOS - optional, for information purposes, basically common metadata. usually full name, office, phone number and email (comma seperated), usually with only name filled.
- home directory path
- shell (program that runs at login) path
- 