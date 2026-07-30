Fully deterministic given seed, and has a default seed.
Can also be broken with low amount of outputs.
## Algorithm
Source is in https://elixir.bootlin.com/glibc/glibc-2.41.9000/source/stdlib/random_r.c#L370
Has multiple implementations inside the source. The used implementation is `TYPE_3`.
The algorithm is also explained in here: https://www.mathstat.dal.ca/~selinger/random/, including a C implementation.
When seeded with `s`, an array `r` is generated:
$$
\begin{matrix}
r_0 = s \\
r_i = (16807 * (\text{signed int}\;r_{i-1}))\ \mathrm{mod}\ (2^{31}-1) \ \text{for i=1..30} \\
r_i = r_{i - 31} \ \text{for i = 31..33} \\
r_i = (r_{i-3} + r_{i-31})\ \mathrm{mod}\ 2^{32} \ \text{for all other i}
\end{matrix}
$$
The output of the `i`th `rand()` call (0 indexed) will be $r_{i+344} >> 1$.
This means the first `rand` will use $r_{344}$, the next one will use $r_{345}$ and so on.
When a seed is not provided with `srand`, the default seed is `1`.
## Breaking
Already implemented, see [[#Python implementation]].
The state can be mostly determined by 31 consecutive outputs, up to the LSB of each `r`.
You can try to determine it by more values, as everything is linear.
Given the state, progressing is easy with $r_i = r_{i-3} + r_{i-31}$
You can also move backward by using the identity $r_{i-31}=r_i-r_{i-3}$.
Remember that the output is the matching r **divided by 2**.
Each state progression is equivalent to a matrix multiplication, so you can determine values far forward or backward by using matrix exponentiation.
## Python implementation
### foresight module
Can be used from python using the `foresight` module.
https://github.com/alschwalm/foresight, clone locally and use `pip install .` to install.
Usage:
```python
from foresight.glibc import random as rand
predictor = rand.from_seed(seed)
predictor = rand.from_outputs([1, 2, 3, ...])

print(next(predictor))
```
### `ctypes` module
Can directly access Glibc methods
```python
import ctypes
libc = ctypes.CDLL("libc.so.6")
seed = 12345
libc.srand(seed)
print(libc.rand())
```