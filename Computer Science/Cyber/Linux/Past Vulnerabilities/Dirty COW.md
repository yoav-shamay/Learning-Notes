Allows to write to arbitrary files, triggering PE.
First, you `mmap` a file as `MAP_PRIVATE` and `PROT_READ` (as you aren't allowed to write to it).
You write to `/proc/self/mem`, see [[Writing to proc mem file]], using [[Copy-on-Write (COW)]] mechanic.
When first loading the file, it loads it to a shared physical read-only memory, and maps the virtual memory there.
When trying to write there, it creates a writable copy. 
The exploit is using a race condition: you call `madvise(MADV_DONTNEED)` to release the writable copy right away, while the `write` still haven't finished.
Afterwards, the `write` retries and asks the kernel again where to write (after the first attempt failed and it created the COW).
As the writable copy was deleted, the kernel gives it the address of the original physical address of the file - allowing you to write arbitrary content.
It is allowed also because the write function dropped the request for writing permission - as it assumed the COW was already created, and now it will write there.
The COW won't be created with write permission as the (user space) program shouldn't be able to write there directly anyway, only kernel writes such as `/proc/self/mem` writes.
## Usage
Can write to any file, allows to get root.
- Write to existing setuid binaries, like /usr/bin/passwd
- write to `/etc/passwd` - add a new user, with uid 0, and a password you know.
- Overwrite VDSO to get RCE on every process that calls `gettimeofday`.