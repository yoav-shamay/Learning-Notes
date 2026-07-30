A common hash. Found to be vulnerable to collision attacks.
## Padding
MD5 has 512 bit (64 bytes) block size.
The padding works as the following:
- A one bit is appended to the end
- Zeros bits are appended to bring the bit length of the message to 64 bits less than a multiple of 512
- The bit length of the unpadded message is added as a 64-bit little endian integer
If the message length is a multiple of 8 bit (full bytes only) you can work in bytes, add `\x01` byte and 0 bytes until the byte length is 8 bytes less than a multiple of 64. The message length added is still in bits though.
## Collisions
MD5 is vulnerable to collisions, which means generating any collision including with known prefix.
Good explanation in https://github.com/corkami/collisions.
### Known collisions
2 blocks:
`TEXTCOLLBYfGiJUETHQ4hAcKSMd5zYpgqf1YRDhkmxHkhPWptrkoyz28wnI9V0aHeAuaKnak`
and
`TEXTCOLLBYfGiJUETHQ4hEcKSMd5zYpgqf1YRDhkmxHkhPWptrkoyz28wnI9V0aHeAuaKnak`
1 block in https://eprint.iacr.org/2010/643.pdf
### Generation with hashclash
Need to install https://github.com/cr-marcstevens/hashclash.
#### No conditions
`md5_fastcoll -o h1.bin h2.bin`.
Collision will be saved in `h1.bin` and `h2.bin`.
#### With a specified common prefix
`md5_fastcoll -o h1.bin h2.bin -p prefix.txt`
Prefix should be saved in `prefix.txt`
Collision will be saved in `h1.bin` and `h2.bin`.
#### With common prefix + custom alphabet
`/mnt/c/programs/hashclash/scripts/textcoll.sh prefix.txt`
Can edit the `textcoll.sh` file to set alphabet.
#### With 2 different specified prefixes
##### fastcpc.sh
Go to `/mnt/c/programs/hashclash/fastcpc_workdir`
and run `../scripts/fastcpc.sh prefix1.txt prefix2.txt`
First time requires a long precompute (~2 hours), but should be faster from second time onwards.
##### cpc.sh
`/mnt/c/programs/hashclash/scripts/cpc.sh prefix1.txt prefix2.txt`
First prefix should be saved in `prefix1.txt` and second one in `prefix2.txt`
Takes a while (2-3 hours)
### Extending Collisions
From the same idea as [[Length Extension Attack]], you can extend an existing collision, if you append the same text (or a different collision).
**Make sure to add padding**.
Formally, if `hash(a) == hash(b)` then `hash(padded(a) | c) = hash(padded(b) | c)`.
And if `hash(c) == hash(d)` then `hash(padded(a) | c) = hash(padded(b) | c) = hash(padded(a) | b) = hash(padded(b) | d)`.
Where `|` is concat.

This can be used to generate a collision with a chosen suffix, or to easily generate a bunch of collision pairs (taking an existing pair and extending it with same text).

You can also generate a triple or more that collides by concat 2 collisions (can be the same collision).