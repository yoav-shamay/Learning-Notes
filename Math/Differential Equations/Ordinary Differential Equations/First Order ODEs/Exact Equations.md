## Definition
An exact ODE is an equation of the form $\phi_X(x, y)dx + \phi_Y(x, y)dy = 0$ where $\phi_X$ and $\phi_Y$ are the partial derivatives of $\phi(x, y)$. $\phi$ is called a potential of the equation.
The solutions of the equations are $\phi(x, y) = 0$
## Finding $\phi$
In order to find the solutions, we compute $\phi(x, y) = \int^x \phi_X(t, y)dt + C(y)$ (where $y$ is treated as a constant in the integration, therefore the "$+c$" is any function depending on $y$).
To find $C(y)$ we find the partial derivative by $y$ of the computed function, compare to $\phi_y$ and solve for $C(y)$. We'll get an equation depending only on $y$, which can be solved simply by integration.
## Exact Equation Criteria
An equation $X(x, y)dx + Y(x, y)dy = 0$ is exact iff $X_y = Y_x$ (partial derivatives).

Formally the conditions for this are:
- $X$ and $Y$  are continuous
- They have continuous partial derivatives $X_y$, $Y_x$ on a valid domain
- $Y \neq 0$ on this rectangle
A valid domain can be for example an open rectangle, but generally any domain that satisfies those:
- every line $y = \text{const}$ that intersects with the domain, the intersection is a segment
- there exists $x_0$ such that in every such segment there's the point $(x_0, y)$
## Integrating Factor
Given the equation $X(x, y)dx + Y(x, y)dy = 0$, a function $\mu(x, y)$ is called an integration factor if $(\mu X)dx + (\mu Y)dy = 0$ is an exact equation.
The new equation is equivalent to the original one, which means finding an integration factor allows us to solve the equation.
To find it, you can try guessing.
The integration factor is the solution for this equation: $Y\mu_x - X\mu_y = (X_y - Y_x)\mu$.

Formally, the functions $X, Y, \mu$ must be continuous and with continuous partial derivatives on a valid domain, see previous section for valid domain definition.
## Integration factor only depending on x or y
- If $\frac{X_y - Y_x}{Y}$ depends only on $x$, then there's an integrating factor only depending on $x$ which is the solution to the [[Linear First Order ODEs]] $\mu'(x) - \frac{X_y - Y{x}}{Y}\mu(y) = 0$.
- If $\frac{X_y - Y_x}{X}$ only depends on $y$, then there's an integration factor only depending on $y$ which is the solution to the [[Linear First Order ODEs]] $\mu'(y) + \frac{X_y - Y_x}{X}\mu(y) = 0$.
