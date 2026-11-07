An analoguous for [[Existence and Uniqueness Theorem]] for first order ODEs.
For an initial value problem
$$
\begin{matrix}
\mathbf{x}' = \mathbf{A}(t)\mathbf{x} + \mathbf{b}(t) \\
\mathbf{x}(t_0) = \mathbf{x}_0
\end{matrix}
$$
Where $\mathbf{A}, \mathbf{b}$ are continuous over an open interval $I \ni t_0$
There exists a unique solution over $I$.

The proof is similar to first order ODEs, using vector functions.
This sequence converges to the solution:
$$
\begin{matrix}
\mathbf{u}_0(t) = \mathbf{x}_0 \\
\mathbf{u}_k(t) = \mathbf{x_0} + \int_{t_0}^t (\mathbf{A}(\tau)\mathbf{u}_{k - 1}(\tau) + \mathbf{b}(\tau)) d\tau
\end{matrix}
$$