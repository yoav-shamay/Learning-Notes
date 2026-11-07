Given $f(x, y)$:
- continuous in a closed rectangle $D = \{(x, y) | \alpha < x < \beta, \gamma < y <\delta\} = (\alpha, \beta) \times (\gamma, \delta)$) (it can be $(-\infty, \infty)$)
- Is [[Lipschitz continuity|Lipschitz continuous]] on $y$ in every closed rectangle $E \subseteq D$ (each rectangle can have a different constant). This is satisfied for example if it has a continuous or bounded partial derivative $f_y$.
and a point $(x_0, y_0) \in D$:
- There exists an interval $I = (a, b) \ni x_0$ with a solution $y = y(x)$ for the initial value problem $y' = f(x, y)$, $y(x_0) = y_0$. 
- Every solution on an open interval $I \ni x_0$, with the graph inside $D$, is unique (if there are two solutions they are equal).
If the partial derivative isn't continuous a solution still exists, but it isn't necessarily unique. 
## Additional details
- Tthere exists a function $y$ defined on a maximal interval $I$, in the sense that it's domain can't be extended for additional values while staying in $D$.
- Finding an exact interval - Given a closed sub-rectangle $K = [x_0 - a, x_0 + a] \times [y_0 - b, y_0 + b]$, where $f(x, y) \leq M$. denote $h = \min(a, b / M)$. then the solution is defined on an open interval containing the interval interval $J = [x_0 - h, x_0 + h]$. This means every such interval is within the maximal interval.
- If $(\gamma, \delta) = (-\infty, \infty)$, then a unique solution exists in the entirety of $(\alpha, \beta)$.
- A sequence of functions converging uniformly (uniformly on $J$) to the solution is:
$$
\begin{matrix}
u_0(x) = y_0 \\
u_n(x) = y_0 + \int_{x_0}^x f(t, u_{n - 1}(t)) dt
\end{matrix}
$$
## Proof Idea
For uniqueness, the idea is to use the required properties to prove any 2 solutions satisfying the conditions are equal

For existence, the idea is that the IVP is equivalent to
$$
u(x) = y_0 + \int_{x_0}^x f(t, u(t)) dt
$$
Which is of the form $u(x) = g(u(x))$, which means we need to find a fixed point.
We start with $u(x) = y_0$ and repeatedly apply $g$ to get closer to the fixed point.
Similar to [[Fixed point iteration]] in Numerical Analysis.
We prove that it really converges to a fixed point in an open interval.
This method isn't really viable to compute the solution, but is useful in the proof.