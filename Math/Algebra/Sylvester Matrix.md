Let $p(x) = p_0 + p_1 x + ... + p_m x^m$ and $q(x) = q_0 + q_1 x + ... + q_n x^n$.
Then the Sylvester Matrix of $p, q$ is the $(n + m) \times (n + m)$ matrix defined as following:
$$
S_{p, q} = \begin{pmatrix}
p_m && ... && p_0 && 0 && ... && 0 && 0\\
0 && p_m && ... && p_0 && 0 && ... && 0 \\
&& && && ... \\
0 && ... && 0 && 0 && p_m && ... && p_0 \\
q_n && ... && q_0 && 0 && ... && 0 && 0 \\
0 && q_n && ... && q_0 && 0 && ... && 0 \\
&& && && ... \\
0 && ... && 0 && 0 && q_n && ... && q_0
\end{pmatrix}
$$
The first $n$ rows are shifted $p_m, ..., p_0$, and the next $m$ rows are shifted $q_n, ..., q_0$.
## Applications
The determinant of the matrix is the [[Resultant]].
It's zero iff the polynomials have a non-trivial gcd because a linear combination of rows resulting in zero indicating of $a(x)p(x) = b(x)q(x)$, for both product being at most degree $n + m - 1$, which means $lcm(p(x), q(x))$ is a smaller degree than $p(x)q(x)$, which indicates a non-trivial gcd.
TODO more applications