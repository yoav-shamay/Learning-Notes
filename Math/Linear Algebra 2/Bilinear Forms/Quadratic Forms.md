## Definition
Given a bilinear form $f: V \times V \rightarrow F$:
- $q(v) = f(v, v)$ is the associated quadratic form of $f$
- $f$ is a polar bilinear form of $q$.
## Symmetric polar form
Every quadratic form has on
e unique symmetric polar bilinear form.
$q(v) = f(v,v)$
$f(v, u) = \frac{1}{2}(q(v + u) - q(v) - q(u))$
## Properties
- $q(v + u) + q(v - u) = 2[q(v) + q(u)]$
- $q(\alpha v) = \alpha^2q(v)$
## Matching matrix
as there's a unique symmetric polar form, and you can take its matrix, there's a unique symmetric matrix representation (given a basis), and you can match a symmetric matrix to a quadratic form.
The matrix is denoted as $[q]_w$.
If $M$ is the transition matrix from $w$ to $w'$ then $[q]_w' = M^t[q]_wM$
## Lagrange method to represent as sum of squares
$f(x_1,...,x_n) = \sum \alpha_{ij}x_ix_j$ 
Based on repeated completing to a square.
Allows to diagonalize a matrix by just converting the matrix to a quadratic form under some basis and in the end taking the representing matrix.
Repeat until no variables remaining:
### Case 1 - $\alpha_{ii} \neq 0$
WLOG assume $i = 1$.
Let's look at every monomial containing $x_1$:
$$
\alpha_{11}x_1^2+2\alpha{12}x_1x_2+2\alpha_{13}x_1x_3 + ... + 2\alpha_{1n}x_1x_n = \alpha_{11}x_1 + 2\sum_{i=2}^n a_{1i}x_1x_i
$$
Complete it to a square:
$$
\alpha_{11}x_1^2 + 2\sum_{i=2}^n a_{1i}x_1x_i = \frac{1}{\alpha_{11}}(\alpha_{11}x_1+...+\alpha_{1n}x_n)^2-\frac{1}{\alpha_{11}}(\alpha_{12}x_2+...+\alpha_{1n}x_n)^2
$$
Denote $y_1 = \alpha_{11}x_1 + ... + \alpha_{1n}x_n$ , $\beta_1=\frac{1}{\alpha_{11}}$.
We'll get $f(x_1,...,x_n)=\beta_1y_1^2 + g(x_2,...,x_n)$
And continue recursively on $g$.
### Case 2 - $\alpha_{ii} = 0$ for each $i$
Replace $x_1,x_2$ with $\frac{1}{2}(x_1+x_2), \frac{1}{2}(x_1-x_2)$
The replacements are:
$2x_1x_2 = (\frac{1}{2}(x_1+x_2))^2 - (\frac{1}{2}(x_1-x_2))^2$
$x_1x_k =  \frac{1}{2}(x_1+x_2)x_k + \frac{1}{2}(x_1-x_2)x_k$
$x_2x_k = \frac{1}{2}(x_1+x_2)x_k - \frac{1}{2}(x_1-x_2)x_k$
Specifically, $\alpha_{11}$ and $\alpha_{22}$ aren't zero.

In short, we'll just swap a variable with a linear combination of previous variables, without making new temporary variables.
You can easily find a representing matrix afterwards.