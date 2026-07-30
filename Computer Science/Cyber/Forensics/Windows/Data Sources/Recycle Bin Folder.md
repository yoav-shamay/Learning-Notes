Each entry in the recycle bin is made out of 2 files: `$I<identifier>` and `$R<identifier>`.
The `$R<identifier>` contains the actual file content.
The `$I<identifier>` contains the metadata, in this format:
- bytes `0-7` - header / version
- bytes `8 - 15` - file size 
- bytes `16 - 23` - deletion timestamp - in FILETIME format, which is amount of 100-nanoseconds since January 1, 1601
- bytes `24 - 27` - path length
- bytes `28-` - original path