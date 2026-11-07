A system of equations of the form
$$
\begin{matrix}
x_1' = a_{11}(t)x_1 + ... + a_{1n}(t)x_n + b_1(t) \\
x_2' = a_{21}(t)x_1 + ... + a_{2n}(t)x_n + b_2(t) \\
... \\
x_n' = a_{n1}(t)x_1 + ... + a_{nn}(t)x_n + b_n(t)
\end{matrix}
$$
Over an interval $I$.
If $b_1 = ... = b_n = 0$, then the system is homogenous.
A linear initial value problem is a system with $n$ initial value conditions:
$$
\begin{matrix}
x_1(t_0) = x_1^0 \\
x_2(t_0) = x_2^0 \\
... \\
x_n(t_0) = x_n^0
\end{matrix}
$$
Where $t_0 \in I$.
Will be most commonly written in matrix form: $\mathbf{x}'(t) = \mathbf{A}(t)\mathbf{x}(t) + \mathbf{b}(t)$
## Homogenous systems
A system is homogenous if $\mathbf{b}(t) = 0$.
- The set of solutions for a homogenous system is a linear space of dimension $n$ over $\mathbb{R}$.
- A basis to the solution space is called a fundamental system of solutions.
- A solution to a homogenous system is the trivial one (all zero) iff it's the zero vector on any point in the domain interval.
- The [[Wronskian#Wronskian of a sequence of function vectors|Wronskian]] of a set of $n$ solutions to a homogenous equation is zero in any point in $I$ iff its zero on the entirety of $I$ iff the set is linearly dependent.
## Non-homogenous systems
For any particular solution $\mathbf{x}_0(t)$ to a non-homogenous system, the set of solutions to the system is exactly the set of the corresponding homogenous system $\mathbf{x}'(t) = \mathbf{A}(t)\mathbf{x}(t)$, plus the particular solution  $\mathbf{x}_0(t)$.
This means solving any non-homogenous system is equivalent to solving a homogenous system and finding a particular solution to the non-homogenous system.