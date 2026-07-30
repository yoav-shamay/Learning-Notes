The [[Osculating Polynomial]] where all $m$ equal 1. It's degree is at most 2n+1.
Can be computed using [[#Formula]] and [[Hermite Interpolation]]. Can also be easily represented as solution for a system of linear equations.
## Formula
$$
H_{2n+1}(x) = \sum_{i=0}^{n} f(x_i)H_{n,i}(x) + \sum_{i=0}^{n} f'(x_i) + \hat{H}_{n, j}(x)
$$
where:
$$
H_{n,i}(x) = [1-2(x-x_i)L'_{n,i}(x_i)]L^2_{n,i}(x)
$$
and
$$
\hat{H}_{n,i}(x) = (x-x_i)L^2_{n,i}(x)
$$
See [[Math/Numerical Analysis/Interpolation/Lagrange Interpolation|Lagrange Interpolation]] for $L$ definition.
Not really good to compute in practice due to the need for a bunch of lagrange polynomials and derivatives, see [[Hermite Interpolation]] for a better algorithm.
## Error of interpolation
If $f \in C^{2n+2}[a, b]$ then:
$$
f(x) = H_{2n+1}(x) + \frac{(x-x_0)^2...(x-x_n)^2}{(2n+2)!}f^{(2n+2)}(\xi(x))
$$
For some (unknown) $\xi : [a, b] \rightarrow (a, b)$.