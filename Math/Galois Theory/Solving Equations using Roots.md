## Root Extension
An extension $K / F$ is called a root extension iff there exists a finite sequence of fields $F = F_0 \subseteq F_1 \subseteq ... \subseteq F_t = K$
Such that $F_i = F_{i - 1}(a_i)$ for $1 \leq i \leq t$ and there exists $n_i \in \mathbb{N}$ such that $a_i^{n_i} \in F_{i - 1}$.
This is equivalent for taking only prime root, as any root can be converted to a sequence of prime roots.
## Polynomial Solvability
A polynomial $f(x)$ is said to be solvable using roots over $F$ if there exists a root extension $K$ that contains the splitting field of $f(x)$.
This means that all roots of $f(x)$ can be expressed using addition, multiplication, division, subtraction, scalars and roots, from $F$.
If $F$ is a field of characteristic zero:
denote $L$ as the splitting field of $f(x)$ over $F$.
Then a polynomial $f(x)$ is solvable using roots iff $G(L, F)$ is solvable.
## Non existence of an equation to solve a polynomial of degree >= 5
If $n \geq 5$ and $F$ has characteristic zero, then the general equation $x^n + a_1x^{n - 1} + ... + a_n = 0$ isn't solvable using roots over $F(a_1, ..., a_n)$.
## Non solvable specific polynomials
- If $p(x)$ is an irreducible polynomial of prime order over $\mathbb{Q}$ with exactly 2 complex roots, then $f(x) = 0$ isn't solvable using roots.
## Additional Properties
Given a field $F$ of characteristic zero, $p$ prime and $n$ a natural number:
- Denote $L$ as the splitting field of $x^p - 1$, then $G(L, F)$ is abelian
- If $F$ contains all roots of $x^n - 1$ and $a^n \in F$, then $F(a)$ is a splitting field of $x^p - a$ and $G(F(a), a)$ is abelian