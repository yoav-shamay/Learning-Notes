Using sagemath:
```python
F = GF(p) # can be any field
R = PolynomialRing(F, 'x')
points = [(5, 8), (3, 7)]
pol = R.lagrange_polynomial(points)
```
This works only on fields, not mod $n$. for modulo $n$:
```python

```
