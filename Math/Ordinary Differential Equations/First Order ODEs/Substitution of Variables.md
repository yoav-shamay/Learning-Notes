A method to solve first order ODEs.
Given an equation of the (standard) form $y' = X(x)Y(y)$, where $X(x)$ is continuous in $(a, b)$ and $Y(y)$ continuously differentiable in $(c, d)$, that is zero in at most a finite amount of points:
- $\int^y \frac{1}{Y(t)} dt - \int^x X(t)dt = C$ on each open interval that the function isn't zero in. Note that the first integral is a function in $y$ and the second one a function in $x$, and this solution is given as an implicit function.
- $y(x) = y_0$ for each $y_0 \in (c, d)$ such that $Y(y_0) = 0$ (those solutions are called singular solutions)

Alternatively, from symmetric form $X_1(x)Y_1(y)dx + X_2(x)Y_2(y)dy = 0$
The solution are:
- $\int^x \frac{X_1(t)}{X_2(t)} dt + \int^y \frac{Y_2(t)}{Y_1(t)} dt = C$
- $y(x) = y_0$ where $Y_1(y_0) = 0$ (singular solutions)

This is derived (not formally) by writing the equation as $\frac{dy}{dx} = X(x)Y(y)$, then changing it to $dy/Y(y) - X(x)dx = 0$
then integrating to get: $\int^y \frac{1}{Y(u)}du - \int^x X(t)dt = C$.
Or from symmetric form by division by $X_2(x)Y_1(x)$ and direct integration.



