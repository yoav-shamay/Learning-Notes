An attack on RSA when $d$ is small, specifically $d < \frac{\sqrt[4]{n}}{3}$.
The bound is non exact - it assumes $p < q < 2p$, and can be smaller / larger depending on other circumstances.
There's a stronger attack called Boneh-Durfee, which works for $d \approx N^{0.292}$.
## Attack Algorithm
Find the continued fraction sequence for $e / n$:
Start with $a = e, b = n, h_0 = 0, h_1 = 1, q_0 = 1, q_1 = 0$
repeat while $b > 0$:
- $t = \lfloor a / b \rfloor$, $r = a \% b$
- set $a, b = b, r$
- set $h_0, h_1 = h_1, t \times h_1 + h_0$
- set $q_0, q_1 = q_1, t \times q_1 + q_0$
- test candidate $h_1, q_1$
If no valid candidate was found, the algorithm fails.

For each candidate $(h, q)$:
- If $h = 0$, reject.
- Set $\varphi = \lfloor \frac{eq}{h} \rfloor$
- Set $p(x) = x^2 - (N - \varphi + 1)x + N$
- Find roots $a, b$ of $p(x)$ - if it doesn't have 2 integer roots, reject
- If $a \times b \neq N$, reject
- Succeed with factors $a, b$ of $N$.
## Proof
Denote $\lambda(N) = \operatorname{lcm}(p - 1, q - 1) = \frac{(p - 1)(q - 1)}{G}$ (on implementations where you use $(p - 1)(q - 1)$, you can pretend $G = 1$).
$ed \equiv 1 \pmod{\lambda(N)}$
Therefore $ed = K \times \lambda(N) + 1 = \frac{K}{G} \times (p - 1)(q - 1) + 1$
denote $\frac{k}{g} = \frac{K}{G}$ the reduced fraction.
Then $ed = \frac{k}{g} \times (p - 1)(q - 1) + 1$.
therefore $\frac{e}{N} = \frac{e}{pq} = \frac{k}{dg}(1 - \delta)$
Where $\delta = \frac{p + q - 1 - \frac{g}{k}}{N}$.
Therefore $\delta < \frac{p + q}{N} < \frac{3}{\sqrt{N}}$ (assuming $p < q < 2p$, which holds if they have same bit count).
Also $ed = \frac{k}{g} \times (p - 1)(q - 1) + 1$ therefore $edg = k(p - 1)(q - 1) + g$.
Therefore $\frac{k}{dg} = \frac{e}{(p - 1)(q - 1)} - \frac{1}{d(p - 1)(q - 1)} < \frac{e}{(p - 1)(q - 1)}$. because $e < (p - 1)(q - 1)$ this is less than 1.
Therefore $|\frac{e}{N} - \frac{k}{dg}| = \frac{k}{dg} \delta < \delta < \frac{3}{\sqrt{N}}$.
For $dg < \frac{\sqrt[4]{n}}{\sqrt{6}}$, we get $|\frac{e}{N} - \frac{k}{dg}| < \frac{3}{\sqrt{N}} < \frac{1}{2(dg)^2}$.
Also we get that $g = edg - k(p - 1)(q - 1)$, therefore $\gcd(k, d)$ divides $g$.
$\gcd(k, g) = 1$ by definition, therefore $\gcd(k, d) = 1$ therefore $\gcd(k, dg) = 1$, so $\frac{k}{dg}$ is reduced.
Therefore from [[Continued Fractions#Legendre's Theorem|Legendre's Theorem]], $\frac{k}{dg}$ appears in the [[Continued Fractions#Simple Continued Fractions|Simple Continued Fraction]] expansion of $e / N$, which depends on entirely known data.
This is the sequence computed in the algorithm (see [[Continued Fractions#Rational $x$|here]] for more details).
This expansion is short (around $O(\log(N))$) because it's exactly the Euclidean Algorithm.

For a candidate $k / dg$:
If $k = 0$ we can immediately reject.
we know $edg = k(p - 1)(q - 1) + g$.
Therefore $\frac{edg}{k} = (p - 1)(q - 1) + \frac{g}{k}$.
$g$ is small therefore most likely $0 < g < k$.
Therefore $\lfloor \frac{edg}{k} \rfloor = (p - 1)(q - 1)$.
Then we compute $p + q = N - (p - 1)(q - 1) + 1$.
And then we compute $(x - p)(x - q) = x^2 - (p + q)x + N$.
We find roots to it using the quadratic formula.
If it has exactly 2 integer roots with product $N$, we know they are $p$ and $q$.
Other methods can be used for verification, like testing if $a^{ed} \equiv a \pmod{N}$.
## Lattice Approach
The key equation is that $|\frac{e}{N} - \frac{k}{dg}|$ is small, at most $\frac{3}{\sqrt{N}}$
This can be rewritten to $edg - kN$ is at most $3dg\sqrt{N}$.
Looking at the lattice
$$
L = \begin{pmatrix}
c && e \\
0 && N
\end{pmatrix}
$$
For a scaling constant $c$.
From the fraction we get the vector $v = (cdg, edg - kN) \approx (cdg, dg\sqrt{N})$.
The optimal pick should be $c = 3\sqrt{N}$. and the norm is $\sqrt{(cdg)^2 + (3dg\sqrt{N})^2} = \sqrt{18Nd^2g^2}$.
The determinant of the matrix is $cN$, so according to gaussian heuristic the expected length of the shortest vector is about $\sqrt{\frac{cN}{\pi e}}$.
Substituting $c$ we get an expected shortest vector of about $0.59N^{3/4}$.
We'll get our vector is smaller than gaussian heuristic for $dg$ below $0.14N^{1/4}$, which gives a strong reason to guess it will be the shortest vector for $dg$ at similar order of magnitude.
There's an actually formal proof with the same bound as given from Legendre's Theorem.
Due to being a 2D lattice, it can be solved using [[Gaussian Lattice Reduction]].
## Implementation
```python
def wiener(e, N):
    e, N = ZZ(e), ZZ(N)
    for c in continued_fraction(e / N).convergents():
        k, D = c.numerator(), c.denominator()
        if k == 0:
            continue
        s = N - e * D // k + 1
        disc = s * s - 4 * N
        if disc >= 0 and disc.is_square():
            t = disc.isqrt()
            p, q = (s + t) // 2, (s - t) // 2
            if p * q == N:
                return int(p), int(q)
```