A general cipher type.
Commonly abbreviated to SPN.
## Components
### S-Box
Substitutes a small block of bits with another block of bits.
Must be invertible.
Each output bit should be changed with 50% probability by every input bit change.
There can be multiple S-boxes in one round or different rounds.
### P-Box (permutation)
A permutation of the bits, shuffles the bit order.
A good P-Box would make the output of one S-Box move to inputs of as many distinct S-Boxes as possible (See [[#Encryption]] for more details).
## Algorithm
### Encryption
There are multiple rounds.
Initialize the State to the plaintext
In each round:
Combine the current round key with the State, usually using XOR.
Divide the State into small blocks, of the size of the S-Box, and apply the S-Box to each block.
Apply the P-Box.

In the end,  so the final S-Box and P-Box application can't be easily reversed and ignored, usually the last P-Box application is omitted, and a final XOR (or other combination) with a subkey is added.

The round keys are usually generated from one key using a Key Schedule process.

Note that order or some details can be different in common variations, this is the general concept.
A visual description:
[![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/SubstitutionPermutationNetwork-en.svg/500px-SubstitutionPermutationNetwork-en.svg.png)](https://en.wikipedia.org/wiki/File:SubstitutionPermutationNetwork-en.svg)
### Decryption
Just the encryption algorithm in reverse.