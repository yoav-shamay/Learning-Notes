A Sturm-Liouville equation is an equation of the form:
$$
(p(x)y')' + (\lambda r(x) - q(x))y = 0
$$
on any interval $I$, where $\lambda$ is a parameter (not a constant), $p, r, q$ are continuous functions on $I$, with $p$ having a continuous derivative.
A Sturm-Liouville problem is a Sturm-Liouville equation with a boundary condition such as $y(a) = 0, y(b) = 0$, where $I = (a, b)$.
## Converting Linear equations to Sturm-Liouville form
Given an equation in the form $X''(x) + P(x)X'(x) + (Q(x) + \lambda R(x))X(x) = 0$
multiply it by $p(x) = e^{\int ^x P(t)dt}$
to get to the form $(p(x)y')' + (\lambda p(x)R(x) - p(x)Q(x))y = 0$.
## Eigenvalues
Given a Sturm-Liouville Problem with the parameter $\lambda$, $\lambda$ is called an eigenvalue of the problem if for $\lambda$ there exists a non-trivial solution $y = \varphi(X)$. $\varphi$ is called an eigenfunction belonging to $\lambda$.
Eigenvalues can be real or complex, but all eigenvalues for regular and periodic problems are real.
## Special Types
### Regular Problems
A regular Sturm-Liouville problem on the interval $[a, b]$ consists of a Sturm-Liouville equation on $(a, b)$, where $p(x), r(x)$ are positive in $[a, b]$ and the following boundary conditions:
- $\alpha y(a) + \alpha' y'(a) = 0$
- $\beta y(b) + \beta'y'(b) = 0$
Where $\alpha$ or $\alpha'$ isn't zero and $\beta$ or $\beta'$ isn't zero.
A solution has to also be continuously differentiable on $[a, b]$.
- Regular problems have infinite eigenvalues $\lambda_1 < \lambda_2 < ...$, with $\lambda_n \rightarrow_{n \to \infty} \infty$.
- All eigenvalues have a real eigenfunction $f(x)$
- All eigenfunctions of the same eigenvalue are of the form $c\times f(x)$.
- Eigenfunctions $f(x), g(x)$ of different eigenvalues are orthogonal in $[a, b]$ under $r$, which means $\int_a^b f(x)g(x)r(x) dx = 0$
### Periodic Problems
A periodic Sturm-Liouville problem on the interval $[a, b]$ consists of a Sturm-Liouville equation on $(a, b)$, where $p(a) = p(b)$, $q(a) = q(b)$, $r(a) = r(b)$ and the boundary conditions are:
- $y(a) = y(b)$
- $y'(a) = y'(b)$
A solution has to also be continuously differentiable on $[a, b]$.
## Sturm-Liouville Operator
The operator is:
$$
L[y] = (p(x)y')' - q(x)y
$$
The input is a function $y$ continuously differentiable twice on $I$ and the output is a function continuous on $y$.
A Sturm-Liouville equation can be written as $L[y] + \lambda r(x)y = 0$
### Lagrange Identity
For 2 functions $\varphi, \psi$:
$$
\varphi L[\psi] - \psi L[\varphi] = (p(\varphi \psi' - \varphi' \psi))'
$$
For regular and periodic problems:
$$
\int_a^b (\varphi L[\psi] - \psi L[\varphi])dx = 0
$$