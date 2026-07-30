Denote:
- $D$ is a unique factorization domain.
- $p(x) = a_0 + a_1 x + ... + a_n x^n \in D[x]$, with $a_n \neq 0$.
- $F$ is the fraction field of $D$.
## Capacity and primitive polynomials
The capacity $c(p)$ of $p(x)$ is defined as $\gcd(a_0, ..., a_n)$.
If $c(p) = 1$ then $p(x)$ is called a primitive polynomial.
## Gauss Lemma and corollaries
- Gauss Lemma: The product of primitive polynomials is a primitive polynomial.
- Corollary: $c(f \cdot g) \sim c(f) \cdot c(g)$
- Corollary: $p(x)$ is irreducible in $D[x]$ iff $p(x)$ is irreducible in $F[x]$.
- Corollary: $D[x]$ is a unique factorization field, and all the factors of a primitive polynomial are primitive.
## Rational root theorem
- If $p(a / b) = 0$ for $a, b\in D$, $\gcd(a, b) = 1$, then $a | a_0$ and $b | a_n$.
- Specifically, if $p(r) = 0$ for $r \in D$, then $r | a_0$ (this is true for every ring)