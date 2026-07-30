`mount --bind old_path new_path`
Can be used for both files and folders.
Uses the `mount` syscall.
Function similarly to symlinks - make the new_path point to old_path
## Differences from symlinks
- Still works even when the file / folder read doesn't follow symlinks.
- Requires root to create.