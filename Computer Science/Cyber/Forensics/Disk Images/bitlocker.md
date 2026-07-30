Windows disk encryption tool.
## Brute force user password
Extract the hash using `bitlocker2john -i file`.
Take the user password hash and save it in a file.
Afterwards use [[Programming/Cyber/Forensics/Hashcat]] to find the password, with mode `22100`.
## Brute force recovery key from list
Can run `dislocker` with every recovery key and see what works.
bitcracker (https://github.com/e-ago/bitcracker) supposed to do it, but couldn't  get to work.

## Bitlocker recovery key properties
Can reduce search space for recovery key.
See: https://github.com/e-ago/bitcracker/issues/45
- Each group of 6 digits is divisible by eleven
- Each group of 6 digits must be less than $720896 = 2^{16} \times 11$
- The sixth digit is checksum: $x_6 \equiv x_1 - x_2 + x_3 - x_4 + x_5 \pmod{11}$. Note that it's equivalent to property 1.
## Opening using user password or recovery key
Use `dislocker <image name> ~/mounted -u`, and then type the password.
Make sure `~/mounted` exists and empty.
Afterwards navigate to `~/mounted`.
The disk image will be there as `dislocker-file`, which can be analysed with any other method.
You can also copy it to another directory so it can be accessed by windows if preferred.