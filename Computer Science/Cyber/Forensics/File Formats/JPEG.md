Image format
## Signature
JPEG usually starts with some segments.
Details about it in https://en.wikipedia.org/wiki/List_of_file_signatures.
The most likely one is `FF D8 FF E0 00 10 4A 46 49 46 00 01
Note that the image also always ends with `FF D9`.
## Segments
A JPEG file consists of a sequence of segments.
Each segment begins with a marker: an `FF` byte, followed by a byte indicating the marker.
Some segments contain just those two bytes, and others has a payload.
Segments with a payload contains two length bytes (high and then low), indicating the length of the payload.
**The length includes the two bytes of the length, but not the two bytes of the marker.**
### Start and End of Image
Segments that are always in an image.
Each image starts with `FF D8` (start of image).
and ends with `FF D9` (end of image).