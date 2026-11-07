ODEs of the form $y^{(n)} + p_{n-1}(x)y^{(n-1)} + ... + p_0(x)y = g(x)$.
## Equivalence to a system of linear first order ODEs
Every linear ODE of order $n$ is equivalent to a system of $n + 1$ linear first order ODEs, by using 
$y_0 = y, y_1 = y', ..., y_n = y^{(n)}$.
The equation system will contain $n$ equations of the form $(y^{(n)})' = y^{(n + 1)}$ for $0 \leq i < n$, and the original equation after substituting every derivative with the new variable.
Therefore all results in [[Linear System of first order ODEs]] apply here, with the Wronskian result matching the definition of [[Wronskian#Wronskian of a sequence of functions|Wronskian of a sequence of functions]].