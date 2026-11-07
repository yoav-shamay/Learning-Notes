## Standard Specification
Given a polynomial $p(x)$ of degree $d$ modulo $n$, finds roots smaller than $n^{1/d}$.
More specifically, a parameter $\varepsilon$ is given, and it finds roots at most $\frac{1}{2}n^{1/d - \varepsilon}$.
The time is polynomial in $\log{n}$,$d$ and $1/\varepsilon$.
Note that the exponents in the polynomials can be large, and slightly decreasing $\varepsilon$ can lead to a very big slowdown.
By brute forcing the first bits you can remove the $1/2$ factor.
TODO learn how it works, uses LLL.
## Unknown factor modulus
Coppersmith also works under an unknown factor modulus.
Given $n$ with a divisor $b \geq n^\beta$ for $0 < \beta \leq 1$, and $f(x) \in Z[x]$ a monic polynomial of degree $d$:
Then you can find all its roots that are smaller than $\frac{1}{2} n^{\beta^2 / d}$.
Specifically for $0 < \varepsilon \leq \beta^7$ it finds roots smaller than $\frac{1}{2} n^{\beta^2 / d - \varepsilon}$
This can be used for example to factor $n$ given most bits of $p$.
## Multivariate version
TODO
## Implementation
Built-in in sage.
```python
coefficients = [0,1,2,3]
Rn = Zmod(n)
Rp = PolynomialRing(Rn, 'x')
pol = Rp(coefficients)
roots = pol.small_roots(epsilon=eps, beta=beta)
print(roots)
```
beta is from [[#Unknown factor modulus]], default for $1$ (standard version).
Note that the bound is less than $n^{1/\deg{p(x)}}$, it just gets closer to it (though can still occasionally find larger roots).
By default `epsilon` is $\beta/8$.
TODO manual implementation can be better?