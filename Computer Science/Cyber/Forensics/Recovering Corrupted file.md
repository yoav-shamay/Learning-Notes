## Corrupted header
Try to look at the header of the file and see if it's similar to a known type.
Full list: https://en.wikipedia.org/wiki/List_of_file_signatures
Try to find the closest and repair it.
See the File Formats directory for specific information about file types.
## Wrong image height / width
In case the image size is vastly different from the actual height times width, try modifying one of them to the (size - header size) / 3 \* (other length) 
(Usually each pixel takes 3 bytes)