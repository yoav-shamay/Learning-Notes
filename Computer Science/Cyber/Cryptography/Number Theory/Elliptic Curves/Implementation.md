## Using sagemath
```python
from sage.all import *
F = GF(Integer(p))
E = EllipticCurve(F, [Integer(a), Integer(b)])
print(E.cardinality())
P = E(-1, 1)
#You can use P + Q, x * P like regular numbers
print(P.order())
#TODO add more (standard curves, example like creating G)
```