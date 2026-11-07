Equations of the form $\mathbf{x}' = \mathbf{A}x$ where $\mathbf{A}$ is a matrix of real constants (not functions).
The solutions are based on the eigenvalues of the matrix.
# Diagonalizable matrices
In this case, we can find a basis of eigenvectors.
### Real Eigenvalues
For each real eigenvalue $\lambda$ of $A$ and a matching eigenvector $\mathbf{v}$, $e^{\lambda t}\mathbf{v}$ is a solution to the system.
### Complex Eigenvalues
For a complex eigenvalue pair $a \pm bi$, where $\mathbf{v}$ is an eigenvector of $a + bi$.
Therefore $\overline{\mathbf{v}}$ is an eigenvector of $a - bi$.
We have this pair of complex solutions:
- $\mathbf{x}(t) = e^{(a + bi)t}\mathbf{v}$
- $\overline{\mathbf{x}}(t) = e^{(a - bi)t}\overline{\mathbf{v}}$.
We can exchange them with this pair of real solutions:
- $\operatorname{Re} \mathbf{x}(t) = \frac{1}{2}(\mathbf{x}(t) + \overline{\mathbf{x}}(t))$
- $\operatorname{Im} \mathbf{x}(t) = \frac{1}{2i}(\mathbf{x}(t) - \overline{\mathbf{x}}(t))$
## Equivalent Linear ODE
Given $p(x) = x^n + a_{n-1}x^{n-1} + ... + a_0$ the characteristic polynomial of $A$, for each solution $\mathbf{x}$ for the ODE, each component $x_i$ of the solution is a solution for the ODE $y^{(n)} + a_{n-1}y^{(n - 1)} + ... + a_0y = 0$.
This means each component $x_i$ is a linear combination of a fundamental system of solutions to this equation, and can be solved by parameterizing the combination.
See [[Homogenous Linear ODEs Solving Techniques#Constant Coefficient Equations|here]] for how to solve the linear ODE.