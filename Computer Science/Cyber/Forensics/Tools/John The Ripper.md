Tool that can extract hashes from encrypted files
TODO add its option to crack directly.
## Getting hash from file
Use `zip2john file.zip`.
Take the hash without the file name for use with [[hashcat]], in the format `$pkzip$...$/pkzip$`
## Tips
- `zip2john` takes the shortest file from the encrypted zip and some checksums, can reconstruct the original shortest file.