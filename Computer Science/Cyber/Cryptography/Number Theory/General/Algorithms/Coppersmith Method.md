Finds small roots of polynomials mod $n$.
Specifically works for roots less than $n^{1/\deg{p(x)}}$.
TODO learn how it works, uses LLL.
### Implementation
Built-in in sage.
```python
coefficients = [0,1,2,3]
Rn = Zmod(n)
Rp = PolynomialRing(Rn, 'x')
pol = Rp(coefficients)
roots = pol.small_roots(epsilon=eps)
print(roots)
```
By default `epsilon` is $1/8 = 0.125$
Setting lower `epsilon` will allow finding higher roots.
Note that the bound is less than $n^{1/\deg{p(x)}}$, it just gets closer to it (though can still occasionally find larger roots).
The runtime gets A LOT SLOWER by lowering epsilon.
`epsilon = 0.06` still runs pretty quickly, and `epsilon = 0.04` takes a few minutes.
