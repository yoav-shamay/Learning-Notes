Using sagemath:
```python
F = GF(p) # can also be something else like reals
R = PolynomialRing(F, 'x')
points = [(5, 8), (3, 7)]
pol = R.lagrange_polynomial(points)
```