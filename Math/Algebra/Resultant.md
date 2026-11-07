The Resultant of 2 univariate polynomials is an expression that's zero iff they have a common root
## Definition Using Roots
Let
$$
\begin{matrix}
f(x) = a\prod_{i=1}^m (x-\alpha_i) \\
g(x) = b\prod_{i=1}^n (x-\beta_i)
\end{matrix}
$$
then:
$$
\operatorname{Res}(f, g) = a^n b^m \prod_{i=1}^m \prod_{j = 1}^n (\alpha_i - \beta_j)
$$
## Computing using coefficients
The Resultant is the determinant of the [[Sylvester Matrix]] of $p, q$.
This is a polynomial expression of the coefficients of $f, g$.

This means for example if $f(x)$ is parameterized using $y$ ($f(x) = h(x, y)$) then the resultant is a polynomial $p$ of degree $n$ with $y$, satisfying $p(y) = 0$ iff $h(x, y)$ has a common root with $g(x)$. 