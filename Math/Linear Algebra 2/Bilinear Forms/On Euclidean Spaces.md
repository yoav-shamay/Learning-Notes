Special theorems on the case of Euclidean spaces.
## Diagonalization using Unitary Diagonalization
- As the representing matrix $A$ is symmetric, there exists unitary $U$ such that $U^{-1}AU = D$ is diagonal.
- As $U^T = U^{-1}$, it also diagonalizes the quadratic form.
## Connection between bilinear forms and linear transformations
For $V$ on $\mathbb{R}$ with an inner product $\langle,\rangle$
- Given a transformation $T$, $\langle Tv, u\rangle, \langle v, Tu \rangle$ are bilinear maps
- Given a bilinear form $f$, there is a unique transformation $T$ satisfying $\langle Tv, u\rangle = f$, and also $\langle v, T^*u\rangle = f$
## Canon form of bilinear/quadratic forms
- Every symmetric matrix from rank $\rho$ is conjugate to a matrix of the form $diag(1,..,1,-1,...,-1,0,...,0)$ where $1$ appears $\pi$ times, $-1$ appears $v$ times and $\pi + v = \rho$.
- This can easily be done by diagonalizing normally, putting all positives before negatives and dividing by sqrt of abs value of each non-zero value.
- Therefore, every quadratic form has a basis where it's represented as $x_1^2 + ... + x_\pi^2 - x_{\pi + 1}^2 - ... - x_{\pi + v}^2$. It's called the canon form.
- Bilinear forms has an equivalent form.
- The form is unique.
## Signature of bilinear/quadratic forms
- The amount of positive and negative coefficients in a diagonal form are the same for each basis.
- The signature of a bilinear / quadratic form is $\sigma = \pi - v$.
- 2 Matrices are conjugate to each other iff they have the same rank and signature.
## Classification of quadratic forms
For $q : V \rightarrow \mathbb{R}$ where $\dim{V} = n$, of rank $\rho > 0$ with $\pi$ positive elements in its diagonal representation:
- Positive definite - $q(v) > 0$ for $v \neq 0$ - iff $\pi = \rho = n$
- negative definite - $q(v) < 0$ for $v \neq 0$ - iff $\pi = 0,\rho = n$
- Positive semidefinite - $q(v) \geq 0$ and exists $v \neq 0$ such that $q(v) = 0$ - iff $0 < \pi = \rho < n$
- Negative semidefinite - $q(v) \leq 0$ and exists $v \neq 0$ such that $q(v) = 0$ - iff $\pi = 0, 0 < \rho < n$
- Not sign preserving - none of the above - iff $0 < \pi < \rho \leq n$
- A quadratic form has a sign iff its representing matrix under some basis has the matching sign.
## Simultaneous Diagonalization
### On quadratic forms
Given $q_1 = X^tAX$, $q_2 = X_tBX$, where $q_2$ is positive definite, then there's a basis $(w)$ satisfying:
$q_1 = \delta_1y_1^2 + ... + \delta_n y_n^2$ ($\delta_1,...\delta_n \in \mathbb{R}$)
$q_2 = y_1^2 + ... + y_n^2$
In other words there's a transformation of the variables that diagonalizes both forms at once.
### On matrices
Given $A, B$ real symmetric matrices where $B$ is positive definite.
Then there's an invertible matrix $M$ satisfying:
$M^t A M$ = $\text{diag}\{\delta_1,...,\delta_n\}$
$M^tBM = I$
## Bound on the result
Can be proved by unitary diagonalization
If $\lambda_1$ is the smallest eigenvalue of the representing matrix and $\lambda_2$ is the largest one, then $\lambda_1 ||v||^2 \leq q(v) \leq \lambda_2 ||v||^2$.