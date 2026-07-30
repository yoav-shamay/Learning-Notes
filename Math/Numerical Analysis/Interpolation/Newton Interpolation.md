An alternative [[Polynomial Interpolation]] algorithm / representation.
Also called newton divided difference interpolation.
Denote the points as $(x_0,y_0),...,(x_n,y_n)$.
The idea is to represent the interpolation polynomial as:
$$
a_0 + a_1(x-x_0) + a_2(x-x_0)(x-x_1) + ... + a_n(x-x_0)...(x-x_{n-1})
$$
The algorithm uses a dynamic programming approach to compute the coefficients $a_0,...,a_n$.
This algorithm allows to add an additional point quickly without recomputing everything again.
## Divided differences
Divided differences are defined recursively:
$f[x_i] = y_i$
$$
f[x_i,...,x_j] = \frac{f[x_{i+1},...,x_j] - f[x_i,...,x_{j-1}]}{x_j - x_i}
$$
Then $a_i = f[x_0,...,x_i]$.
## The algorithm
Define $F_{i,j} = f[x_{i-j},...,x_i]$.
For $i$ from 0 to $n$:
Set $F[i,0] = y_i$
For each $j$ from 1 to $i$:
set
$$
F_{i,j} = \frac{F_{i,j-1} - F_{i-1,j-1}}{x_i - x_{i-j}}
$$
In the end, return $F_{0,0},...,F_{n,n}$.
## Connection between divided differences and derivatives
For $f \in C^n[a, b]$, and $x_0, ..., x_n \in [a, b]$, then there exists $\xi \in (a, b)$ such that $f[x_0,...,x_n] = f^{(n)}(\xi) / n!$.
## Forward and Backward difference formula
Applicable when $x_i = x_0 + hi$ for some $h \in \mathbb{R}$.
Denote $s = \frac{x - x_0}{h}$.
Also denote for any real $s$ (not just natural):
$$
\binom{s}{k} = \frac{s(s-1)...(s-k+1)}{k!}
$$
Then:
$$
P_n(x) = \sum_{k = 0}^{n} \binom{s}{k}k!h^k f[x_0,...,x_k]
$$
And more importantly:
$$
P_n(x) = \sum_{k=0}^{n}\binom{s}{k}\Delta^kf(x_0)
$$

Similarly, where $x_i = x_n + (n - i)h$, and $s = \frac{x - x_n}{h}$ then:
$$
P_n(x) = \sum_{k=0}^{n} (-1)^k \binom{-s}{k} \nabla^k f(x_n)
$$
See [[Notation]] for delta and nabla notation meaning.
