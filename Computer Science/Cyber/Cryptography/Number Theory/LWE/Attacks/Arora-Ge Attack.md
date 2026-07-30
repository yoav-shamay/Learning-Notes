This attempts to solve the LWE problem directly, which means recovering $s$ from a bunch of equations with errors.
This attack applies when there is a small amount of options for each error ($x$). 
In this case, we will replace each equation of the form $(a, s) + e = b$, where $e \in {e_0, ..., e_x}$, to this equation: $((a, s) - b + e_0)(a, s - b + e_1)...((a, s) - b + e_x) = 0$.
Solving a bunch of polynomials is NP hard, however there are several ways to do it if we have enough equations.
## Linearization
This method requires at least $n^x$ different points.
This isn't a linear equation, however we can use the [[Linearization]] trick, which means replacing each multiplication of $k$ variables with its own variable, so the equation is linear.
If we have $n^x$ equations, we should still have enough data to solve this system, and recover $s$.
## Grober basis
TODO