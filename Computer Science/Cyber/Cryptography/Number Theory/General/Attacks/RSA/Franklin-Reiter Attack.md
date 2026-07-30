An attack on RSA.
If you have $x^e$ and $p(x)^e$ for some known polynomial $p(x)$, you can recover $x$.
Originally meant for small $e$ (like $e=3$), but viable for larger $e$ (even $e=65537$, with half-gcd implementation).
Denote:
$$
\begin{matrix}
ct_1 = x^e \\
ct_2 = p(x)^e
\end{matrix}
$$
## The Attack
The idea is to look at the polynomials $x^e-ct_1$ and $p(x)^e-ct_2$
We will look at their `gcd`, which will most likely only be $x$.
Note that over a ring the standard Euclidean algorithm might fail.
## Implementation
```python
from sage.all import *
R = PolynomialRing(Zmod(n), 'x')
X = R.gen()
pol1 = X ** e - ct_1
pol2 = (2 * X + 1) ** e - ct_2
g = gcd(pol1, pol2)
root = -g[0] / g[1]
```
Replace the `gcd` with an actual function call, also replace the polynomials with a `pari` version in case of half gcd.
For GCD implementation, see [[Polynomials in sagemath#Polynomial gcd]].
Use Euclidean algorithm for small e and use a more efficient algorithm with pari for larger e.