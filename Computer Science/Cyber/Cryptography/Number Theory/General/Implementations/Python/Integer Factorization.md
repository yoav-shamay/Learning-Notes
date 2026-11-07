Using sage `factor` function:
```python
```python
from sage.all import *
factors = factor(num)
```
output is list of tuple of `(prime, exp)`.
## Elliptic Curve Factorization
Faster for many small factors
```python
from sage.all import *
factors = ecm.factor(6)
# factors = [2, 3]
```