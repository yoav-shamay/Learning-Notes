Image format
## Header
The signature, which is always the same is the first 8 bytes and it's 89 50 4E 47 0D 0A 1A 0A
## Chunks
Each chunk has 4 bytes length, 4 bytes name, content and then 4 bytes CRC.
You can view chunks and errors using `pngcheck -v image`
#### IHDR
The first chunk must be IHDR with 13-bytes length, which means the bytes 8-16 have to be: 
00 00 00 0D 49 48 44 52
The content (next 13 bytes) of the IHDR is the following:
width (4 bytes)
height (4 bytes)
bit depth (1/2/4/8/16) (1 byte)
color type (0/2/3/4/6) (1 byte)
compression method, is 0 (1 byte)
filter method, is 0 (1 byte)
interlace method (0/1) (1 byte)
In total it's 25 bytes