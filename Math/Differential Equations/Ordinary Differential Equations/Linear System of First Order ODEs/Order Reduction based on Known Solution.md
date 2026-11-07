For homogenous systems, if you know one (non-trivial) solution for the system, you can reduce the order of the system by 1.
Given an equation $\mathbf{y}' = \mathbf{A}y$ and a solution $\mathbf{z}$, we'll substitute:
$$
\begin{matrix}
y_1 = x_1 - \frac{z_1}{z_n}x_n \\
... \\
y_{n - 1} = x_{n - 1} - \frac{z_{n - 1}}{z_n}x_n \\
y_n = \frac{1}{z_n}x_n
\end{matrix}
$$
The new system:
- decomposes to a system of $n - 1$ equations on $n - 1$ variables + one additional equation on the final variable
- Has $\mathbf{e}_n$ as a solution
By solving the system of $n - 1$ equations, and using the final one to find $y_n$, we will get $n - 1$ linearly independent solutions.
Adding $\mathbf{e}_n$ as a solution will give a full fundamental system of solutions.