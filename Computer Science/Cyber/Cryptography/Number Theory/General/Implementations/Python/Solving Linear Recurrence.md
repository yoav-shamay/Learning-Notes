Can be done using matrix exponentiation, see [[Matrices in sagemath]] for general matrix details.
TODO more sagemath options (direct formula?)
## Using sympy
```python
import sympy
# Define the function using sympy's symbols.
y = Function('y')
f = y(n+4) - 21 * y(n+3) - 301 * y(n+2) + 9549 * y(n+1) - 55692 * y(n)
# Solve the recurrence equation using `rsolve` with the given initial conditions.
equation = rsolve(f, y(n), {y(0): 1, y(1): 2, y(2): 3, y(3): 4})
print(equation)
```
Will give a direct formula (unlike matrix exponentiation)