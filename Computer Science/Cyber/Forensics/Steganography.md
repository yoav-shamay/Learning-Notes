Hiding data in images
TODO split
## Tools
- aperisolve - all in one, has online version, also look at common passwords (can have password other users entered)
- binwalk
- zsteg. In case image is too large use `RUBY_THREAD_VM_STACK_SIZE=500000000 zsteg <img>`
- https://georgeom.net/StegOnline/image - stegsolve online basically
- stegsolve (you can use arrows to manipulate color pallete, try all options).
- exiftool (metadata)
- steghide (all image types and audio types, has passphrase but can use empty one)
- Checking for extra data in the end of `jpeg`: `python3 -c "import sys; d=open(sys.argv[1],'rb').read(); print(d[d.rfind(b'\xff\xd9')+2:].hex())" "FILE_NAME"` (doesn't get automatically detected using other tools)
- https://futureboy.us/stegano/compinput.html - compare 2 images
- stegseek - steghide brute, allows to check if a file has steghide encryption using `stegseek --seed`
## Random tools
- Ask an AI for tools for the format used, for example: `Can you suggest 10 steg tools that output bmp image` (if I have a password for example might want to mention it).
- https://stylesuxx.github.io/steganography/
- `openstego` - `bmp, png`
- https://futureboy.us/stegano/decinput.html - `jpeg, wav, au` (untested)
- try all tools under https://daniellerch.me/stego/intro/tools-en/
- If a tool is mentioned in the metadata, try opening in it / reading about it
## Tips
- svg is human-readable, try looking for text elements
- Try reverse image search maybe the image is taken from somewhere that will hint.
- Try to look at xxd and find unusual byte patterns, usually in the end.
- grayscale images should follow r == g == b, try to figure out where it's not
- Challenge name or description might hint, for example if it's quant search `jpeg quant` or `image quant` or `steganography quant` and look at multiple results, and maybe ask GPT.
- Check the header, it might be different
- Check if there are unused bits / bytes in the format / encoding, try to use them
- Try to google `<format> steganography`
- Try to convert to another format on which a common tool like `steghide` works, if it's loseless.
## LSB Steganography
A binary number is encoded in the LSB of the RGB values of the pixels of of the image.
Can be in the LSB of one color or a combination of them.
The combination can be an order of them (r then g then b for example) or the and/xor/or of the colors.
zsteg checks for most options.
The secret is usually put in the beginning of the image.
## Multiple Images
You can try to combine multiple images using operations:
- xor
- or
- and
- different pixels
- difference
- abs difference
- sum (mod 256)
The most likely one is `xor` or different pixels
You can also try to apply a transformation to one of the images before combination:
- rotation
- transpose
- mirror on an axis
You can brute force all options if it seems random and check everything, or just try to notice patters that seem like one of those fits when looking at both images at once.
## PDFs
Can contain hidden text. to reveal:
- Press Ctrl + A and copy everything
- Use https://www.pdffiller.com/ - will show hidden textboxes
- open in foxit reader that allows selecting hidden text
https://tools.pdf24.org/en/extract-images - can extract images in pdf, exactly, can steg on them.
## Unicode

### Unicode tag plane
Unicode characters `0xe0000-0xf00000` - a special purpose 16-bit long plane
By just using the ASCII equivalent in this plane, this can be used to hide characters.
To decode:
```python
for x in res:
    print(chr(ord(x) - 0xE0000), end='')
```
### High unicode characters
a generalization for the previous one.
Just take the lower byte in some high unicode characters to get some ASCII byte.
Note that high bytes might be encoded using [[Unicode Surrogate Characters]].
