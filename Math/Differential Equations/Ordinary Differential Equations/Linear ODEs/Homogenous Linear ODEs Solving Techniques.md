All the solutions are of the form $C_1y_1 + C_2y_2 + ... + C_ny_n$ where $y_1, y_2, ..., y_n$ are linearly independent solutions.
## Constant Coefficient Equations
Special case of [[Constant Coefficient Homogenous systems|this technique on linear systems]], which is much simpler here.
Equations of the form $c_ny^{n} + c_{n-1}y^{n - 1} + ... + c_0y = 0$.
The solutions are derived from guessing a solution of the form $e^{\lambda x}$, giving the polynomial equation $p(\lambda) = c_n\lambda^n + ... + c_0 = 0$.
Solve the equation (if quadratic can using the quadratic formula).
For a real root $\lambda$ there's the solution $e^{ax}$
For a pair of complex roots $z = a + bi$, $\overline{z} = a - bi$ there are the solutions $e^{ax}\cos{bx}$, $e^{ax}\sin{bx}$.
If a root has multiplicity $m$ and gives the solution $f(x)$, there are the solutions $f(x),xf(x), ..., x^{m - 1}f(x)$ (for complex each pair has the same multiplicity, so for both solutions of the pair).
This gives $n$ solutions which are all linearly independent.
## Order Reduction Based on Known Solution
Special case of [[Order Reduction based on Known Solution|this technique on linear systems]], which is much simpler here.
If we already found a solution $y_1(x)$ for the equation, substitute $y = y_1z$.
This will lead to a [[Missing Equations|Type I Missing]] ODE of order $n$ which will lead to a homogenous linear ODE of order $n - 1$.
If we find $n - 1$ solutions we will end up with a [[Linear First Order ODEs|Homogenous Linear First Order ODE]] which is solvable.
Note that even if the equation is non homogenous, this method will still reduce the order anyway.