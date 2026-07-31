Also called standard form of ODEs.
An equation of the form $y^{(n)} = f(x, y(x), y'(x), ..., y^{(n-1)}(x))$.
$n$ is called the order of the ODE.
All ODEs discussed in those notes are explicit.
## Initial Condition
An initial condition for the equation is a condition of the form:
- $y(x_0) = y_0$
- $y'(x_0) = y_1$
- ...
- $y^{(n-1)}(x_0) = y_{n-1}$
where $(x_0, y_0, y_1, ..., y_{n-1})$ is in the domain of $f$.
An ODE with an initial condition is called Initial Value Problem.
## Formal Definition of Solution
A function $y(x)$ is a solution to the ODE in the range $I = (a, b)$ if:
- $y(x)$ is differentiable $n$ for all $x \in I$
- $f$ is defined for $x, y(x),y'(x),...,y^{(n-1)}(x)$ for all $x \in I$
- $y^{(n)}(x) = f(x, y(x),y'(x),...,y^{(n-1)}(x))$ for all $x \in I$
