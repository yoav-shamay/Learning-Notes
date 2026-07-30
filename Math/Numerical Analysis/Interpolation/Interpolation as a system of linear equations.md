Given $n + 1$ points $(x_i, y_i)$, denote $p(x) = \sum a_i x^i$
Then interpolation can be represented as the following system of linear equations:
$$
\begin{matrix}
a_0 x_0^0 + ... + a_nx_0^n = y_0 \\
... \\
a_0 x_{n+1}^0 + ... + a_n x_{n+1}^n = y_{n+1}
\end{matrix}
$$
It can be solved to find $p(x)$.
In practice, this method is bad as the errors are big, however it can be useful in special cases like some coefficients are known or over a finite field.