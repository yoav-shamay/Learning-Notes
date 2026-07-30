An attack on block ciphers, specifically for [[Substitution-Permutation Network]] (or similar ciphers).
A known plaintext attack - requires a (large) set of `pt, ct` pairs, that aren't chosen by the attacker.
The idea is to find linear formulas - of the type $x_1 \oplus x_2 \oplus ... \oplus x_n \oplus y_1 \oplus y_2 \oplus ... \oplus y_m = 0$  where $x_i$ are input bits and $y_j$ are output bits, that has a high or low probability of happening.
We'll call the difference of the expression as the bias and denote it as $\varepsilon$.
Those approximations differentiate the cipher from random.
## Piling-Up Lemma
For independent random binary variables $x_1,x_2,...,x_n$ such that $P(x_i = 0) = 1/2 + \varepsilon_i$:
$P(x_1 \oplus x_2 \oplus ... \oplus x_n = 0) = 1/2 + 2^{n-1}\prod_{i=1}^n\varepsilon_i$
This is useful in computing the probability of a complex linear expression from multiple components.
## Constructing Linear Approximation
First, we will construct linear approximations for each of the S-Boxes.
This can be done by brute-forcing all possible linear approximations assuming the S-Boxes are small enough.
We'll try to find approximations with large bias (in abslute value).
We can chain multiple approximations through multiple rounds by following the permutation. 
TODO - how to construct a path
Subkey bits are ignored due to being constant.
We assume each recurrence is independent to compute the total bias using the [[#Piling-Up Lemma]].
This may not be true, but works well in practice.
## The Attack
The idea is to each time recover some bits from the final round subkey.
Each time we chain multiple recurrences to get a recurrence involving the input for the final application (involving a p box then xor with subkey).
The recurrence will depend on some subkey bits, but due to being constant we ignore them and therefore we dont know the bias sign (positive or negative).
Then we brute force all possibilities for the final subkey bits that are relevant to the final sboxes including the recurrence.
For each plaintext and ciphertext pair, we xor the ciphertext with the guessed subkey bits, reverse apply those sboxes and count how many times the linear recurrence we found is satisfied.
The bits with the count that deviates the largest amount from half is assumed to be correct (as wrong ones are assumed to behave randomly). We cant know the sign to expect the bias due to unknown previous subkey bits.
We repeat the attack to fully recover all subkeys.
Every time we fully recover the final subkey, we can reverse apply the final round. We can also ignore the final permutation step in the previous round by permutating the ciphertext and subkey.
## Required plaintext count
A good approximation for the required plaintexts for an expression with bias $\varepsilon$ is $1/\varepsilon^2$.
Generally, the more the better.
## Linear Hulls
Most likely won't matter for the attack itself. 
There may be multiple options to select a path to get the same linear approximation. In this case, the independence assumption fails, and the real probability may be higher or lower than expected from the [[#Piling-Up Lemma]].
In practice though usually a path with high biases dominates the hull, and it's unlikely that another path will cancel it.
## Implementation
TODO - how to perform in practice.