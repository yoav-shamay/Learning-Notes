Works in a general ring, which means also modulo $n$
Using sagemath:
## Defining Polynomial
```python
F = GF(p)
R = PolynomialRing(F, 'x') # mod p
R = PolynomialRing(Zmod(n), 'x') # mod n
pol_coefficients = [3, 1, 2] # 2 * x^2 + x + 3
pol = R(pol_coefficients)
X = R.gen()
pol = X ** 5 - 3 # X^5 - 3
```
## Roots of polynomial
- `pol.roots(multiplicities=False)`
- `pol.any_root()` - faster, returns any root instead of all
An optimization:
You can first compute the `gcd` of `pol` with `x^p - x` (mod `pol`) in order to reduce the polynomial to a multiplication to linear factors, like this:
```python
X = R.gen()
g = power_mod(X, p, pol) - X
pol = gcd(pol, g)
```
## Polynomial gcd
`res = gcd(pol1, pol2)`
Only works mod `p`.
For general ring:
### Euclidean algorithm code
```python
def pol_gcd(a, b):
    while b != 0:
        a, b = b, a % b
    return a.monic()
```
### Efficient implementation from `pari`
```python
from sage.all import *

R = PolynomialRing(Zmod(n), 'x')
X = R.gen()

f1 = pari(f"{Mod(x,{n})^{e}-{c1}")
f2 = pari(f"({a}*Mod(x,{n})+{b})^{e}-{c2}")
res = pari.gcd(f1, f2).sage({"x": X})
```