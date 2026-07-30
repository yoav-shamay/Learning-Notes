Using sage:
```python
field = GF(p)
field = GF(p ** 2)
root = field.zeta(n)
assert root ** n == 1
```