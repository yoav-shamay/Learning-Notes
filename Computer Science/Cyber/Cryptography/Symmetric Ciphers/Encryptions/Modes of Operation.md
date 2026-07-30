For Block Ciphers, after dividing the plaintext to blocks, decide how to extend the encryption from one block to the entire message.
### ECB mode
Encrypt every block independently.
Vulnerable to "ECB penguin attack".
For example when an image is encrypted if you give a color to every block (same color to same block) you can still see patterns in the image.
In addition you can combine multiple encrypted blocks to get unintended encrypted text.
## CTR mode
Randomly choose 16-byte message called IV (that will be outputted along the ciphertext).
for the Kth block, encrypt IV + k and XOR it with the according block of the plaintext. The output is the matching block of the ciphertext.
The sequence of encrypted IV, IV+1,... is a Pseudo random sequence. plaintext ^ pseudo-random-sequence = ciphertext.
If IV is reused with known plaintext you can immediately decipher, and even without the plaintext you can know the xor of 2 plaintexts.
## CBC mode
A 16-bit random IV is generated, will be outputted along the ciphertext.
Each plaintext block is XORed with the previous encrypted block and then encrypted.
The first block is XORed with the IV instead.
Vulnerable to [[Padding Oracle Attack]]
## GCM mode
In addition to the encryption, GCM mode generates a MAC, which is a small hash that verifies the data integrity, that in order to create you need the key.
Because of the verification using MAC is immune to decryption oracle.
### Encryption
GCM mode encryption and decryption is very similar to [[#CTR mode|CTR]], where the counter is concatenated (as 32-bit counter) to the IV. The IV is 12-byte and the counter is 4-byte, together they are 16-byte.
### The MAC
Each block is 128-bits and is treated as an element of `GF(2^128)` (addition in this field is the XOR of the bits).
`H` is computed, which is the encryption of the block of 128 zeros.
The MAC is computed for 2 parts: a stream A of unencrypted plaintext (associated data) divided into blocks and a stream C of encrypted ciphertext.
We line up `A | C | len(A) | len(C)` where `len(A)` is the length of the plaintext and `len(X)` is the length of the **unpadded** text X.
Then we look at it as a polynomial where the coefficient of the highest power is the first block and the lowest power $x^0$ is the last block.
Then the MAC is the result of evaluating the polynomial in H.
To compute it we multiply first block by `H`, add the second block, multiply by `H` again, add the third one and so on.