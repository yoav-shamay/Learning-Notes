A method to find root of a function $f(x)$.
Parameters: initial approximations $p_0, p_1$, tolerance $TOL$, maximum amount of iterations $N_0$.
This is similar to [[Newton-Raphson Method]] but uses an approximation to compute the derivative - $f'(p_n) \approx (f(p_n) - f(p_{n - 1})) / (p_n - p_{n - 1})$
## Algorithm
Start with $q_0 = f(p_0)$, $q_1 = f(p_1)$
Set $p_n = p_{n - 1} - q_{n - 1}(p_{n - 1} - p_{n - 2})/(q_{n - 1} - q_{n - 2})$
And $q_n = f(p_n)$.
Stop when $|p_n - p_{n - 1}| < TOL$ successfully and return $p_n$.
Also stop after $N_0$ iterations (as failure).
## Convergence order
This method converges with order $\alpha = (1 + \sqrt{5}) / 2$.