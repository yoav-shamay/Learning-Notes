Can decrypt ciphertext and encrypt plaintext from padding validation oracle.
Works on CBC encryption.
## Implementation
Automatically performed using the padding-oracle library
See https://pypi.org/project/padding-oracle/
## Decrypting a block
You discover each byte of the plaintext, one by one.
For each byte, brute force all options.
If it's the right byte, the (plaintext prefix plus this byte, and something random for everything else) xor (necessary padding for the size) as IV, and the ciphertext block as ciphertext will have a valid padding.
If not, then it will be invalid.
There is a small chance that there will be multiple valid options (when this is the first byte, and the next plaintext byte is equal, so both paddings of length 1 and 2 will be valid).
In this case you can just swap the next byte with other random thing and test the possible options again. Only when will be possible.
## Decrypting whole ciphertext
Decrypt each block, and xor the plaintext with the previous encrypted block (IV in the case of first block).
## Encryption
First, divide the plaintext to blocks.
Now create the ciphertext blocks in reverse order:
For the last block, choose something random.
Now for every block, decrypt it. Now you need to xor it with something to create the corresponding plaintext block.
This will be the previous block.
Repeat for each plaintext block.
The first block in the result will be the IV and the second block onwards will be the ciphertext.