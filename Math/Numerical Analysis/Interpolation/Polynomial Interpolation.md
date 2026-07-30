Polynomial interpolation is defined as following:
Given $n + 1$ points on the plane $(x_i, y_i)$, find the polynomial $p(x)$ of degree (up to) $n$ passing through all those points (satisfying $p(x_i) = y_i$).
It can be proven that there always exists exactly one such polynomial.
## Error of interpolation
Provides a bound for the error between the interpolation polynomial constructed from $n$ points of a function to the real function, on a closed range.

Given $f(x)$ having $n+1$ continuous derivatives on the range $[a, b]$, and distinct  $x_0, ..., x_n \in [a, b]$, denote $P(x)$ the interpolation polynomial of $(x_0, f(x_0)), ..., (x_n, f(x_n))$.
Then for each $x \in [a, b]$ there exists $\xi(x) \in [\text{min}(x_0, ..., x_n), \text{max}(x_0, ..., x_n)]$ (and therefore in $[a, b])$ such that:
$$
f(x) = P(x) + \frac{f^{(n+1)}(\xi(x))}{(n+1)!} (x-x_0)(x - x_1)...(x - x_n)
$$
## Algorithms
- [[Math/Numerical Analysis/Interpolation/Lagrange Interpolation|Lagrange Interpolation]] - provides a direct formula
- [[Interpolation as a system of linear equations]] - bad in practice, however useful in some special cases
- [[Newton Interpolation]] - can be more accurate and allows more easily to add points.