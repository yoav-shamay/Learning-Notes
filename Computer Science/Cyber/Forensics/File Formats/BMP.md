Image format
## Headers
### First Header
42 4D
Size of file - 2 bytes
00 00 00 00 (can be other things)
offset in 4 bytes (10 + size of second header), usually 36 00 00 00
### Second Header
There are multiple types. the most common one is BITMAPINFOHEADER.
#### BITMAPINFOHEADER
size of header in 4 bytes: 28 00 00 00
width in 4 bytes
height in 4 bytes
01 00
bits per pixel in 2 bytes, usually 18 00
compression method (4 bytes)
horizontal resolution - pixels per meter (4 bytes)
vertical resolution - pixels per meter (4 bytes)
number of colors in the palette (0 if 2 ^ pixels per color, usually this) (4 bytes)
number of important colors (0 when every color is important) (generally ignored, usually 0) (4 bytes)