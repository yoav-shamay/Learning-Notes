A polynomial interpolation method. Provides a direct formula for the interpolation polynomial.
Given $n + 1$ points $(x_0, y_0), ..., (x_n, y_n)$:
Define:
$$
L_{n, k}(x)
 = \prod_{i=0, i \neq k}^{n}{\frac{x - x_i}{x_k - x_i}}
 =  \frac{(x - x_0)...(x - x_{k - 1})(x - x_{k + 1})...(x - x_n)}{(x_k - x_0)...(x_k - x_{k - 1})(x_k - x_{k + 1})...(x_k - x_n)}
$$
It's the polynomial of degree $n$ satisfying $L_{n,k}(x_i) = 0$ for all $i \neq k$ and $L_{n, k}(x_k) = 1$.
Then the interpolation polynomial is $p(x) = y_0 L_{n, 0}(x) + ... + y_n L_{n, n}(x)$.