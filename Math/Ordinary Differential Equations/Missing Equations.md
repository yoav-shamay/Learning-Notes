If the equation is independent in $x$ or in $y(x)$, the order of the equation can be reduced.
Applicable to ODEs of order at least 2.
## Type I
Equations of the form $y^{(n)}(x) = f(x, y'(x), ..., y^{(n-1)}(x))$ (independent of $y$).
We'll substitute $z(x) = y'(x)$.
This reduces the equations to an equation of order $n-1$:
$z^{(n-1)}(x) = f(x,z(x),z'(x),...,z^{(n-2)}(x))$.
The solution for this equation will be $y'$, we can then integrate to find the solution for $y$.
If it's an initial value problem, all conditions on $y'(x_0),...,y^{(n-1)}(x_0)$ can be substituted with identical conditions on $z(x_0), ..., z^{(n-2)}(x_0)$.
The constant of the integration can be determined by the condition on $y(x_0)$.
If in addition to $y$ also $y',...,y^{k-1}$ are missing, we can substitute $z(x) = y^{(k)}(x)$ to reduce the order by $k$.
## Type II
Equations of the form $y^{(n)}(x) = f(y(x), ..., y^{(n - 1)}(x))$ (independent of $x$), assuming $y'(x) \neq 0$ in the domain. This also guarantees the function is invertible.
Like Type I, we'll substitute $z(x) = y'(x)$.
According to chain rule: $z'(y) = \frac{dz}{dy} = \frac{dz}{dx}\frac{dx}{dy}$
And $x'(y) = 1/y'(x) = 1/z(y)$. Therefore $z'(y)z(y) = \frac{dz}{dx}$
Therefore: $y''(x) = z'(x) = \frac{dz}{dx} = z'(y)z(y)$.
Where in $z'(y)$ we mean derivative according to $y$ and where $y = y(x)$, it exists as the function is invertible.
Similarly we can get:
$$
y^{(n)}(x) = z^{(n - 1)}(x) = d(z^{(n-2)})/dx = \frac{dz^{(n-2)}}{dx} = \frac{dz^{(n-2)}}{dy}\frac{dy}{dx}
$$
Repeated differentiation according to this equation allows to get all derivatives of $y$, replacing them with an expression based on $z(y)$, with largest derivative being of order 1 smaller than $n$.
So now we got an ODE of order $n - 1$ on $z(y)$.
Solving it will give us $z(y)$.
To get $y$ as a function of $x$ we can solve the [[Substitution of Variables|separable first order ODE]] $y'(x) = z(y)$.