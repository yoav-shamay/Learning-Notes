Linux saves the entire disk, including all the filesystem, in `/dev`.
Requires root or group `disk`.
## Finding file name
Always in `/dev`.
You can get the host root file system disk using `cat /proc/cmdline`. those are the parameters passed to the kernel at boot. Look for `root=/dev/smth`.
Alternatively look for drives in `/dev` or guess `/dev/sda1`.
## Mounting
`mount /dev/sda1 /mnt`.
Afterwards you can `chroot` to the mounted filesystem to get real RCE.
## Reading and Writing
Alternatively, you can read/write from this file like any other file.
This is like a disk image, can be analysed using tools such as [[sleuthkit]] or [[autopsy]].
Writing there will modify the real disk itself.
## Usages
- container escape
- bypassing filename or similar blacklists - can just read the entire disk.
- 