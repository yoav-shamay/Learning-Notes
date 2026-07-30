A method to find root of a function $f(x)$.
Parameters: initial approximations $p_0, p_1$, tolerance $TOL$, maximum amount of iterations $N_0$.
Similar to [[Bisection Method]] but instead of bisecting in the middle, passes a line between the range boundaries and bisects at it's intersection with the $x$ axis.
Also similar to [[Secant Method]] (computes the same value) but bounds the root each time in a range.
## Algorithm
Maintain a range $[l, r]$ where $sign(f(l)) \neq sign(f(r))$
Each time choose $p = r - f(r)(r - l)/(f(r) - f(l))?$
If $|p - r| < TOL$ return $p$ (success).
If $p$ has a different sign than $r$ set $l = p$, otherwise set $r = p$.
After $N_0$ iterations fail.