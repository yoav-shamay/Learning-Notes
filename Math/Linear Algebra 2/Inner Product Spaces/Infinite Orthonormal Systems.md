A set of vectors in a inner product space is an Orthogonal System if every 2 elements are orthogonal.
A Orthogonal System is Orthonormal iff the norm of every vector  is 1.
## Gram Schmidt
Gram schmidt works the same for infinite set of linearly independent vectors $u_i$.
The series will be defined by induction, with:
$$
v_{n + 1} = u_{n + 1} - \sum_{k = 1}^n (u_{n + 1}, w_k)w_k
$$
and
$$
w_{n + 1} = \frac{v_{n + 1}}{|v_{n + 1}|}
$$
With $w_i$ being an equivalent orthonormal system.
## Properties
- Every orthonormal system is linearly independent (an infinite set is linearly independent if every finite subset is linearly independent)
## Bessel Inequality
Given $(u_k)_{k \geq 1}$ an orthonormal system in an inner product space $V$, then for each $v \in V$:
$$
\sum_{k = 1}^{\infty} |(v, u_k)|^2 \leq |v|^2
$$
Therefore
$$
\lim_{n \to \infty} (v, u_n) = 0
$$
## Fourier series
The Fourier Series of a vector $v$ under an orthonormal system is:
$$
\sum_{k = 1}^\infty (v, u_k)u_k
$$
The [[Fourier Series]] used in Real Analysis is the Fourier series on the linear space $RI[-\pi, \pi]$ (all Riemann integrable function, with two functions that are equal almost anywhere being treated the same) with the standard inner product, and the trigonometric basis $\{1/\sqrt{2\pi}, \cos(kx)/\sqrt{\pi}, \sin(kx)/\sqrt{\pi}\}$ (which is a complete basis)
## Complete Orthonormal System
An orthonormal system is called a complete orthonormal system if it's an orthonormal system and for each $v \in V$, it's Fourier series converges to $v$ (under the natural norm).
or alternatively:
$$
|v - \sum_{k = 1}^n (v, u_k)u_k| \to_{n \to \infty} 0
$$

The following conditions are equivalent for a system being complete:
1 - Parseval Equality - for each $v \in V$:
$$
|v|^2 = \sum_{k = 1}^{\infty} |(v, u_k)|^2
$$
2 - the span of $u$ is dense in $V$ - for each $v \in V$ and $\varepsilon > 0$ there exists $n \in N$ and scalars $\gamma_1, ..., \gamma_n$ such that:
$$
|v - \sum_{k = 1}^n \gamma_ku_k| < \varepsilon
$$
