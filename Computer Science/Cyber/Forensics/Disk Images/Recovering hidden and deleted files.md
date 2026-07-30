## Recovering deleted files
Use `sudo foremost -i disk.img -o ~/carved_files`
## Finding embedded files
Use `binwalk disk.img` to find embedded files, compressed data and etc.
It is good for uncovering hidden files, though is worse than other tools for normal scan.
You can use the `-e` files to extract detected items automatically.
## Slack Space
After each file in a disk image there's unused space (slack space) that might hide data.
You can view it by manually finding the address of the file and viewing using `xxd` for example.
You can also show it in `Autopsy` by pressing the settings button and unchecking the `Hide slack files` options.