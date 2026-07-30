Normally used to reduce size of executables, also extremely obfuscates them. Can be reversed.
## Detecting packing type
- `Detect It Easy (DiE)` - a tool to automatically detect packer type.
- `strings` might include a relatively long string stating its packed and the tool type
- Try to unpack using common tools like UPX
## UPX
Unpack using `upx -d file -o file_unpacked`