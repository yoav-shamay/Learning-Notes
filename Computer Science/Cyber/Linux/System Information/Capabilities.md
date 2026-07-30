In linux, full root permissions are split into multiple partial capabilities.
On some cases, such as docker containers, you may have only partial capabilities as root.
See https://man7.org/linux/man-pages/man7/capabilities.7.html for more info
## File capability sets
Each executable has its own capability set that will affect the capabilities it will gain, in addition to the parent capability sets.
- Permitted - these capabilities are automatically added to the process permitted regardless of the parent process inheritable capabilities.
- Inheritable - this is ANDed with the parent process inheritable set to determine the inheritable capabilities.
- Effective - not a set but a bit, that if set all capabilities from permitted will be moved to effective.
See [[#Computing children capabilities]] for more information about how each set affects the child capabilities.
### Viewing and editing file capabilities
You can view file capabilities using the `getcap <file>` command.
If you have the `CAP_SETFCAP` capability you can set capabilities using the `setcap 'cap_name=sets_letters' <file>` command
For example: `setcap cap_net_raw=ep /usr/bin/ping`.
## Process capability sets
Each process has 5 capabilities sets:
- Permitted - The capabilities that you may add to your effective capabilities.
- Inheritable - capabilities that will be passed to children created using `execve`.
- Effective - the actual set of capabilities used for permission checks.
- Bounding capabilities - Hard bound for the capabilities of the process and children. Capability not in the bounding cannot be gained in any way.
- Ambient capabilities - Capabilities that will be passed to children, even of non-privileged processes.
See [[#Computing children capabilities]] for more information about how each set affects the child capabilities.
## Change process capabilities
### Effective, inheritable and permitted
This can be done using the `capset` syscall, though preferred to use `cap_set_proc` from `libcap`.
The new effective set must be a subset of the new permitted set.
The new inheritable set must be a subset of `existing_inheritable & bounding`
The new permitted set must be a subset of the existing permitted set.
If the process has `CAP_SETPCAP` capabilities, you have no limitations except the bounding set.
### Ambient
Can be modified using the `prctl` system call.
Ambient capabilities are automatically removed if the matching capability is removed from the permitted and inheritable capabilities.
TODO limitations and permissions required
### Bounding
Can be modified using the `prctl` system call.
TODO limitations and permissions required.
## Child process capabilities
When parent process (`P`) does `execve` of file (`F`), the child process (`P'`) capability sets will be the following:
`P'(ambient) = (file is privileged) ? 0 : P(ambient)`
`P'(permitted) = (P(inheritable) & F(inheritable)) | (F(permitted) & P(bounding)) | P'(ambient)`
`P'(effective) = F(effective)? P'(permitted) : P'(ambient)`
`P'(inheritable) = P(inheritable)`
`P'(bounding) = P(bounding)`
## Checking your capabilities
`cat /proc/self/status | grep Cap`.
You can decode it using `capsh --decode=hex_number`.
Alternatively just use `capsh --print` if it's installed.
Should run as root (using `sudo` for example).