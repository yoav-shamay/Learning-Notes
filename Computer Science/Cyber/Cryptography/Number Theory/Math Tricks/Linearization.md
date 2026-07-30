The idea is that if we have a system with some non-linear components (like a system of quadratic equations), but we have way more equations than variables, we can replace each non-linear component with its own variable.
If we still have at least as much equations as variables, we can solve the new linear system, and then verify that the added varaibles actually match the constraint.
Example:
$$
\begin{matrix}
x + y + xy = 1 \\
2x + 3y + 5xy = 2 \\
y - 6x + 8xy = 3
\end{matrix}
$$
We can substitute $z = xy$ to get a linear equation system, we have 3 equations and 3 variables so we can solve it, and then verify that $z$ is indeed $xy$.
Even if we have enough equations, this doesn't always work, for example in this case:
$$
\begin{matrix}
xy = 3 \\
xy^2 = 4
\end{matrix}
$$
