Prefer other methods over this, tools are generally better.
Look at each partition separately and look at it's start and end.
Find the byte offset (sector offset * 512)
Use `sudo mount -o loop,ro,offset=<byte-offset> disk.img ./res_directory`

Alternatively: use `sudo losetup --show -f -P disk.img`
Then the partition devices will be `/dev/loop0p1`, `/dev/loop0p2` and so on (not necessarily `loop0`, depends on the output)
Then use `sudo mount -o ro /dev/loop0p1 ./res_diectory`
## Corruption repair
In case of a `can't read superblock` error, you should try to repair the filesystem. Use `file` on the partition device and if it's `ext4` for example repair it this way: `sudo fsck.ext4 -f /dev/loop0p3`