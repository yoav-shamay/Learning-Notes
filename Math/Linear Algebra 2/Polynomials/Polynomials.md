### $\text{gcd}$ and $\text{lcm}$
- $\text{gcd}$ of polynomials is the  polynomial monic dividing all polynomials and every other divisor divides it.
- It exists and unique
- It's the only polynomial monic that is a common divisor and has no common divisor of larger degree.
- Denote the gcd of $P_1,...,P_n$ as $H$. There exists $Q_1,...,Q_n$ such that $H = P_1Q_1 + ... + P_nQ_n$.
- Given $P_1,...,P_n$, $I = \{Q_1P_1 + ... + Q_nP+n | Q_1,...,Q_n \in F[x]\}$ is a linear subspace of $F[x]$ and it's exactly all multiples of the gcd.
- $P_1,P_2$ are coprime if their gcd is 1
- The $\text{lcm}$ is the smallest common multiple (in degree)
- It exists and unique
- Every other multiple divides the $\text{lcm}$.
- Denote the leading coefficient of $P_1,P_2$ as $c$. $c^{-1} P_1 P_2 = \text{lcm}(P_1(x),P_2(x)) \gcd(P_1(x),P_2(x))$ (and the $\text{lcm}$ is the only polynomial satisfying this)
## Irreducible polynomials
- $P(x)$ is irreducible if $Q(x)R(x) = P(x) \implies \deg{Q(x)} = 0$ or $\deg{R(x)} = 0$
- A polynomial of degree 2 or 3 is reducible iff it has a root
- A real polynomial of degree at least 3 is reducible (because if $\lambda$ is root then $\overline{\lambda}$ is also a root)
- If $P(x)$ is irreducible and $P(x) | Q(x)R(x)$ then $P(x)|Q(x)$ or $P(x)|R(x)$
## Decomposition
- Every polynomial $P(x)$ with leading coefficient $c$ can be represented as $P(x) = cP_1(x)P_2(x)...P_k(x)$ where $P_i(x)$ is monic and irreducible.
- This representation is unique up to order.
- $P(x) | Q(x)$ if the set of polynomials in the decomposition of $P(x)$ is a subset of $Q(x)$ and all powers are less or equal.