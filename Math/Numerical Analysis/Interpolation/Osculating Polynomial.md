Given $n$ points $x_0, ..., x_n$, natural numbers $m_0, ..., m_n$ where $m = \text{max}(m_0, ..., m_n)$, and a function $f \in C_m[a, b]$:
The osculating polynomial approximating $f$ is the unique polynomial $p(x)$ of least degree satisfying $f^{(i)}(x_j) = p^{(i)}(x_j)$ for each $0 \leq j \leq n$ and $0 \leq i \leq m_i$.
It's degree is at most $n + \sum m_i$.
Can be computed using [[Hermite Interpolation]]. Can also be easily represented as solution for a system of linear equations.