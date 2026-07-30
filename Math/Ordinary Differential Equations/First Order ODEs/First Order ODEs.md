An equation of the form $y' = f(x, y(x))$, which is called an explicit ODE (or standard form of the ODE).
For example, $y' = 5xy(x) + \sin{y(x)^2} + 3x$.
## Initial Condition
An initial condition for the equation is a condition $y(x_0) = y_0$, where $(x_0, y_0)$ is in the domain of $f$.
An ODE with an initial condition is called Initial Value Problem.
## Formal Definition of Solution
Denote the equation $y' = f(x, y(x))$. A function $y(x)$ is a solution to the ODE in the range $I = (a, b)$ if:
- $y(x)$ is differentiable for all $x \in I$
- $f$ is defined for $x, y(x)$ for all $x \in I$
- $y'(x) = f(x, y(x))$
## Existence and Uniqueness Theorem
Given $f(x, y)$ continuous in a closed rectangle $D = \{(x, y) | \alpha < x < \beta, \gamma < y <\delta\}$) and with a partial continuous derivative $f_y$, and a point $(x_0, y_0) \in D$:
- There exists a range $I = (a, b) \ni x_0$ with a solution $y = y(x)$ for the initial value problem $y' = f(x, y)$, $y(x_0) = y_0$.
- Every solution on any range $I$ including $x_0$ is unique (if there are two solutions they are equal).
If the partial derivative isn't continuous a solution still exists, but it isn't necessarily unique. 
## Symmetric form
The equation in the form $X(x, y)dx + Y(x, y)dy = 0$ (where derivative is $dy / dx$).
From the standard from, $\frac{dy}{dx} y(x) = f(x, y)$, we get $f(x, y)dx - dy = 0$.
To the standard form, we get $y' = dy/dx = -\frac{X(x, y)}{Y(x, y)}$.