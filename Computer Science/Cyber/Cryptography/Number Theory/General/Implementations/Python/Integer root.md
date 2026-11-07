## Square Root
Returns floor of square root
```python
import math
sqrt = math.isqrt(n)
sqrt = isqrt(n) # sagemath
```
## General Root
Using sagemath:
```python
res = Integer(n).nth_root(m) # exact root, raises exception if doesn't exist
# res ^ m = n
res, is_perfect = Integer(n).nth_root(m, truncate_mode=True) # floor of root
# is_perfect = True if it's exact, false if not
```
