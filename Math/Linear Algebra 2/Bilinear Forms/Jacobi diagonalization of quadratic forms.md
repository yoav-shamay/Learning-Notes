## Theory
- A minor of the matrix is the determinant of the matrix given by removing some rows and columns
- A principle minor is a minor where we remove rows and columns of same indices
- A leading principal minor is a principle minor where we remove a suffix of rows and columns (basically a square prefix)
- Given $q = X^t A X$ representation on basis $w = (w_1, ..., w_n)$, and $A = [\alpha_{ij}]$ satisfies that all leading principal minors aren't 0, then there's $(u) = (u_1,...,u_n)$ such that $q$ is represented as $q = \frac{\Delta_0}{\Delta_1}y_1^2+...+\frac{\Delta_{n-1}}{\Delta_n}y_n^2$ ($\Delta_0 = 1$)
- This is called the Jacobi representation of $q$
- $u_i = \beta_{i1}w_1 + ... + \beta_{ii}w_i$
- $\beta_{k1},...,\beta_{kk}$ satisfies:
$$
\begin{matrix}
\alpha_{11}t_1 + \alpha_{12}t_2 + ... + \alpha_{1k}t_k = 0 \\
\alpha_{21}t_1 + \alpha_{22}t_2 + ... + \alpha_{2k}t_k = 0 \\
... \\
\alpha_{k-1,1}t_1 + \alpha_{k-1,2}t_2 + ... + \alpha_{k-1,k}t_k = 0 \\
\alpha_{k,1}t_1 + \alpha_{k,2}t_2 + ... + \alpha_{k,k}t_k = 1
\end{matrix}
$$
The determinant of the equation is $\Delta_k \neq 0$.
- if $q(v) \neq 0$ for $v \neq 0$ then all the leading principal minors are non-zero.
## Consequences (on Euclidean Spaces)
- $q$ quadratic form, with representing matrix $A$ under some basis, is positive definite iff all principal leading minors of $A$ are positive.
- It's positive semidefinite if all principal leading minors are non-negative.