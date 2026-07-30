## Square Root
Using builtin math:
Returns floor of square root
```python
sqrt = math.isqrt(n)
# sqrt ^ 2 = n
```
## General Root
Using sagemath:
Returns exact root, raises exception if doesn't exist
```python
res = Integer(n).nth_root(m)
# res ^ m = n
```
Using gmpy2:
Returns floor of root
```python
res, exact = gmpy2.iroot(n, m)
# res ^ m = n
# exact stores if it's an exact root
```