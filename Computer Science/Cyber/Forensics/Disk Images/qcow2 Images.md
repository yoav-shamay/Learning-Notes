Virtual machine image format used by QEMU
## Mounting
See https://unix.stackexchange.com/questions/674017/get-a-raw-disk-image-from-qcow2
Run:
```bash
sudo modprobe nbd max_part=16
sudo qemu-nbd -c /dev/nbd0 img.qcow
sudo mount /dev/nbd0p1 /mnt
```
Replace `p1` with the right partition number/
To undo:
```bash
sudo umount /mnt
sudo qemu-nbd -d /dev/nbd0
sudo modprobe -r nbd
```
## Converting to raw image file
`qemu-img convert -O raw img.qcow`
## Running
### virt-manager
Create new VM in virt-manager and select `Use existing Disk Image`.
Select the file, and the OS (can choose generic or mount it to see).
Then run the VM.
### VirtualBox
Create a new VM, don't select ISO image. 
Select the OS similarly.
Expand Specify Virtual Hard Disk
Select Use Existing Virtual Hard Disk File
Select the file
Create the VM