In order to view images saved in process memory (like mspaint).
To do this change extension to `.data` and then open in gimp (can by dragging).
Experiment with RGB / RGBA, width / height, offset.
Common widths to try: 500, 1000, 512, 615 (appeared), 1024, 1920, 1080, 1152, 648.
I can use large widths / heights, you can scroll in the preview.
Try very large height and just scroll instead of setting offset.
If common widths doesn't work, try increasing width by 100 each time until noticing something visible, and then trying smaller increases (like 10).
Width should be exactly the image width to work, or very close. In order to find it try increasing slowly, should be a multiple of 100 or at least 10.

First find the large white square with large width (3000 worked for me) then try to reduce width if smaller. if it's not too far into the file I can just manually offset / increase height for smaller widths otherwise I should approximate the offset and use `dd` before trying lower offsets.
Gimp caps offset at 524288 and height around 32700, so if it doesn't work I might want to use `dd` to manually generate larger offsets, this way:
`dd if=mspaint.data of=offset.data bs=1M skip=150 count=100 status=progress`
block size of 1M bytes, skip = how many blocks to skip, count = how many blocks to include
Other settings should be default (RGB 8 bit though might want to try RGBA, unsigned, little endian, contiguous).

After finding the image I might need to flip / rotate, use Image -> Transform