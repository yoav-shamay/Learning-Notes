A method to find a root of a function $f(x)$.
Really good in practice (converges very fast).
This algorithm requires existence (and computability) of $f'(x)$ and that $f'(p_n) \neq 0$.
Parameters: initial approximation $p_0$, tolerance $TOL$, maximum iterations $N_0$.
## Algorithm
Set $p_{n + 1} = p_n - f(p_n)/f'(p_n)$
Stop when $|p_{n+1} - p_n| < TOL$ (successfully, return $p_{n+1}$)
Stop after $N_0$ iterations passed (failure).
## Convergence Criteria
For $f$ a range $[a, b]$, if:
- $f(p) = 0$
- $f'(p) \neq 0$
There exists $\delta \neq 0$ such that for each $p_0 \in [p - \delta, p + \delta]$ then the sequence $p_n$ converges to $p$.
Useful in theory but not in practice as we can't determine $\delta$.
## Order of Convergence
If $f(p) = 0$ and $f'(p) \neq 0$, for sufficiently small $|p_0 - p|$, the method will converge at least quadratically to $p$.