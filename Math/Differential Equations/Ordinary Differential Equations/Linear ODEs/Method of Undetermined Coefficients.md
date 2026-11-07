A method to solve non-homogenous equations with constant coefficients, of the form $a_ny^{(n)} + ... + a_0 = g(x)$.
This method involves guessing a (parameterized) solution based on $g(x)$, then getting an equation / system of equations for the parameters involved in the guess. Solving it will give the particular solution.
For various types of $g(x)$, there's a guaranteed form of a particular solution.
Note that the homogenous version is a [[Homogenous Linear ODEs Solving Techniques#Constant Coefficient Equations|constant coefficient equation]], meaning the solutions are based on the roots of the corresponding polynomial $p(x) = a_nx^n + ... + a_0 = 0$. 
In all the following cases, $P_m(x)$ is a polynomial of degree $m$.
### $g(x) = P_m(x)$
Denote $k$ as the smallest number such that one of $a_0, ..., a_k$ isn't zero (equivalent to the multiplicity of $0$ as a root of $p(x)$).
Then there's a solution of the form $y_p = x^k(E_mx^m + ... + E_0)$.
### $g(x) = P_m(x)e^{kx}$
Denote $a$ as the multiplicity of $k$ as root of $p(x)$. 
Then there's a solution of the form $x^a(E_m x^m + ... + E_0)e^{kx}$.
$a$ is equal to the smallest natural number such that $x^a e^{kx}$ isn't a solution to the corresponding homogenous equation (equivalence of the multiplicity of $k$ as a root of $p(x)$).
This is derived by substituting $y = e^{kx}f(x)$, which returns to [[#$g(x)$ is a polynomial|the previous case]].
### $g(x) = P_m(x)e^{kx}\sin{\delta x}$ or $g(x) = P_m(x)e^{kx}\cos(\delta x)$
Denote $a$ as the multiplicity of $k \pm i\delta$ as root of $p(x)$.
There's a solution of the form $x^a e^{kx}((a_m x^m + ... + a_0)\cos{\delta x}) + (b_m x^m + ... + b_0)\sin{\delta x})$.
Alternative complex derivation:
$e^{(k + i\delta)x} = e^{kx}\cos{\delta x} + ie^{kx}\sin{\delta x}$.
Therefore we will find a root for the equation with $g(x) = P_m(x) e^{(k + i\delta)x}$, and then take the real part of the complex solution for $\cos$ or imaginary part for $\sin$.
There's a solution (to the new equation) of the form $x^a(E_mx^m + ... + E_0)e^{(k + i\delta)x}$.
It's equivalent, however doing the derivatives on the complex functions might be easier.