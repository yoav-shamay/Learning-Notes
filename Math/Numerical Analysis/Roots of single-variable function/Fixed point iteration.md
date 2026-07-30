An algorithm to find fixed points of a function in a range.
Can be used to find roots, by finding a fixed point of another function, like $f(x) + x$.
The convergence speed depends on the chosen function.
The parameters are $p_0$ (initial point), $g$ (function), $TOL$ - tolerance, $N_0$ (maximum iterations)
The algorithm can find a fixed point or fail.
## Algorithm
Start with $p_0$ and set $p_n = g(p_{n-1})$.
Stop and return $p_{n+1}$ once $|p_{n+1} - p_n| < TOL$ 
Fail once $N_0$ iterations has passed (to prevent the algorithm from running indefinitely).
## Convergence criteria 1
When for a range $[a, b]$:
- $g$ is defined over the entire range
- For every $x \in [a, b]$, $g(x) \in [a, b]$
- $g'$ is defined on $(a, b)$
- There exists $0 < k < 1$ such that $|g'(x)| \leq k$ for each $x \in (a, b)$
- $p_0 \in [a, b]$
There's a unique fixed point $p$ for $g$ in the range $[a, b]$ and the algorithm converges to it.
The error is bounded using $|p_n - p| \leq k^n \text{max}(p_0 - a, b - p_0)$
Under this criteria is method converges only linearly (order 1) with error constant $|g'(p)|$
## Convergence criteria 2
For $p = g(p)$, if:
- $g'(p) = 0$ 
- $g''$ is continous with $|g''(x)| < M$ in an open interval containing $p$
Then with $p_0$ close enough to $p$, this method converges (at least) quadratically to $p$, with error constant at most $M/2$.
This is less well defined (the range where it happens isn't determined) but guarantees quadratic convergence.
