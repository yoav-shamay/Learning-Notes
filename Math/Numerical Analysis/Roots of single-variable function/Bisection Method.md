A method of finding a root of a function $f(x)$.
We start with a range $[l, r]$ where $\text{sign}(f(l)) \neq \text{sign}(f(r))$.
By the middle value theorem, there's a root in this range
Each time we pick the middle $(l + r) / 2$ and pick the edge with opposite sign to it, halving the range.
Each time the range length get halved.
We stop once we find a root ($f(mid) = 0$), or once the range is small enough (after a constant amount of iterations).
The absolute error after $n$ iterations with initial range $[a, b]$ is bounded by $(b - a) / 2^n$ (as that's the size of the range).
## Convergence order
This method coverges linearly (order $1$) with error constant $1/2$.