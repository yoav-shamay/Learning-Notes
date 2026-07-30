Can be used to cut large files easily.
Usage:
`dd if=<input file> of=<output file> <options>`
Options:
- `bs=<block size>` amount of bytes per block, will be multiplied by the amounts used in the other options. **Defaults to `512` (not one byte!)**.
- `skip=<blocks to skip>` - starting position (in blocks), amount of blocks to skip
- `count=<block count>` - length of segment (in blocks), amount of blocks to take from input file.