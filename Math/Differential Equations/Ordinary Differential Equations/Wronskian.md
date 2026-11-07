## Wronskian of a sequence of functions
The Wronskian of $n$ functions $f_1, ..., f_n$ that are differentiable $n - 1$ times is:
$$
W(f_1,...,f_n;x) = \begin{vmatrix}
f_1(x) && f_2(x) && ... && f_n(x) \\
f_1'(x) && f_2'(x) && ... && f_n'(x) \\
... && ... && ... && ... \\
f_1^{(n - 1)}(x) && f_2^{(n - 1)}(x) && ... && f_n^{(n - 1)}(x)
\end{vmatrix}
$$
If $f_1, ..., f_n$ are linearly dependent on a closed interval $I$, then $W(f_1, ..., f_n ; x) = 0$ for each $x \in I$.
So this can be used to show linear independence of functions on a range (If $W(x_0) \neq 0$ for $x_0 \in I$).
Note that this is only one direction, $W(x) = 0$ for all $x \in I$ doesn't guarantee that the functions are linearly dependent.
This is a special case of the next definition, using the vectors of the derivatives of the functions.
## Wronskian of a sequence of function vectors
Given $n$ function vectors $\mathbf{x}_1(t), ..., \mathbf{x}_n(t)$ of length $n$,
$$
W(\mathbf{x}_1, ..., \mathbf{x}_n; t) = 
\begin{vmatrix}
x_{1,1}(t) && ... && x_{1,n}(t) \\
... && ... && ... \\
x_{n,1}(t) && ... && x_{n,n}(t)
\end{vmatrix}
$$
In other words, the determinant of the matrix where its columns are $\mathbf{x}_1(t), ..., \mathbf{x}_n(t)$.
If $\mathbf{x}_1(t), ..., \mathbf{x}_n(t)$ are linearly dependent on a closed interval $I$, then $W(\mathbf{x}_1, ..., \mathbf{x}_n ; t) = 0$ for all $t \in I$.
This implication is only one direction.