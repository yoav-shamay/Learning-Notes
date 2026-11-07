Given $n, e, d$, we know that $k = ed - 1$ is divisible by $(p - 1)(q - 1)$.
Denote $k = 2^s \times t$.

The idea is to randomly sample an element until we get an element that is a quadratic residue modulo $p$ but not modulo $q$. therefore $x^s$ (maybe after squaring a few times) will be 1 modulo $p$ but -1 modulo $q$, leading to $x^s - 1$ being divisible by only $p$ and only $q$.
## Algorithm
1. Compute $t = ed - 1$
2. While $t$ is even, divide it by 2
3. Select random $2 \leq g < n$
4. Compute $x_0 = g^t \pmod n$
5. Set $x_n = x_{n - 1}^2 \% n$, and stop in $x_n = 1$.
6. If $\operatorname{gcd}(x_{n - 1} - 1, n)$ is a non-trivial factor, we factored $n$. If not, go back to step 3.
## Implementation
Built in in pycryptodome:
```python
from Crypto.PublicKey import RSA
key = RSA.construct((n, e, d))
p, q = key.p, key.q
```