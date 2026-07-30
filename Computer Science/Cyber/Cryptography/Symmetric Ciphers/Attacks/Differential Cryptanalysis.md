https://www.ioactive.com/wp-content/uploads/2015/07/ldc_tutorial.pdf
An attack on block ciphers, specifically for [[Substitution-Permutation Network]] (or similar ciphers).
A chosen plaintext attack - requires the attacker to be able to encrypt arbitrary plaintexts.
For 2 inputs $X_1$ and $X_2$ with outputs $Y_1$ and $Y_2$:
We'll define the input difference $\Delta X = X_1 \oplus X_2$.
We'll define the output difference $\Delta Y = Y_1 \oplus Y_2$.
We'll call the pair $(\Delta X, \Delta Y)$ a differential.
The attack exploits differentials with a high probability of occurance (much higher than the expected $1/2^n$).
## Constructing differentials
First, we'll construct differentials for the sboxes.
For each sbox, if it's small enough, we can brute force all possible input pairs and count each output difference.
The subkey xor has no influence on the differentials as its xored for both inputs in the pairs.
The P box simply permutates the output differential.
TODO finish and implementation, how to do in practice