## Symmetric Polynomials
A polynomial on multiple variables that any permutations on the variables doesn't change it, over a field $F$.
### Elementary symmetric polynomials
Every symmetric polynomial is a polynomial expression in the elementary symmetric polynomials, which are:
$$
\begin{matrix}
t_1(n) = \sum x_i \\
t_2(n) = \sum_{i < j} x_ix_j \\
t_3(n) = \sum_{i < j < k}x_i x_j x_k \\
... \\
t_n(n) = x_1...x_n
\end{matrix}
$$
Which means an expression involving field scalars, multiplication and addition only.
### Properties
- The set of all symmetric polynomials in $F[x_1, ..., x_n]$ is a subring of it.
- The leading element of a product of symmetric polynomials is the product of the leading elements of the polynomials
## Symmetric Rational Functions
A rational function on multiple variables that any permutations on the variables doesn't change it, over a field $F$.
This is identical to all the rational functions in elementary symmetric polynomials, $F(t_1, ..., t_n)$.
### Properties
- The set of all symmetric polynomials in $F(x_1, ..., x_n)$ is a subfield
- Any permutation on the variables on $F(x_1, ..., x_n)$ is an automorphism, which means this is the intersection of all the fixed fields of those automorphisms.