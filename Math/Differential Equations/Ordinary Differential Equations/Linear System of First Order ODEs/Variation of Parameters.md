Method to find a particular solution to a non-homogenous [[Linear System of first order ODEs]], which can then be used to find a full solution.
Given a system $\mathbf{x}' = \mathbf{A}(t)\mathbf{x} + \mathbf{b}(t)$, and $\mathbf{x}_1(t), ..., \mathbf{x}_n(t)$ a fundamental system of solutions to the corresponding homogenous system.
There's a solution of the form $\mathbf{x}(t) = \sum_{i=1}^n C_i(t)\mathbf{x}_i(t)$
Where $C_1, ..., C_n$ are functions that their derivatives can be found by solving the system of linear equations $C_1'(t) \mathbf{x}_1(t) + ... + C_n'(t)\mathbf{x}_n(t) = \mathbf{b}(t)$.
Then $C_1, ..., C_n$ themselves can be found by integration.