## Definition
Linear form is a linear transformation $s : V \rightarrow F$ For $V$ linear space on $F$.
A bilinear form is a transformation $f: V \times V \rightarrow F$ that for every constant $v \in V$, $f(v, x), f(x,v)$ are linear forms.
Alternatively, a bilinear form is a transformation $f: V \times V \rightarrow F$ satisfying:
- $f(v_1 + v_2, u) = f(v_1, u) + f(v_2, u)$
- $f(\lambda v, u) = \lambda f(v, u)$
- $f(v, u_1 + u_2) = f(v, u_1) + f(v, u_2)$
- $f(v, \lambda u) = \lambda f(v, u)$
For example: on $\mathbb{R}$ (euclidean spaces) inner product is a bilinear form (but on unitary spaces it's not).
## Bilinear polynomial
- A bilinear homogenous polynomial is a polynomial $p(x_1,...,x_n;y_1,...,y_n) = \sum \alpha_{ij}x_iy_j$ (where all $\alpha$ are scalars).
- Alternatively, $p(X,Y) = X^tAY$ for vectors $X,Y$
- This means every such polynomial is defined uniquely by a matrix (and opposite)
Every bilinear form is equivalent to a matching bilinear polynomial, and therefore to a matrix (given a basis).
For a linear space $V$ on $F$ with a basis $w$:
- Given a bilinear homogenous polynomial $p = X^tAY$, $f(v, u) = [v]_w^tA[u]_w$ is a bilinear form.
- This $f$ satisfies $f(w_i, w_j) = \alpha_{ij}$
- Every bilinear form $f$ is of the form $f(v, u) = [v]_w^TA[u]_w$
- For a single $A = [\alpha_{ij}] = [f(w_i, w_j)]$.
- This $A$ is denoted as $[f]_w$.
- If $M$ is the transition matrix from $w$ to $w'$, then $[f]_{w'} = M^t[f]_wM$.
- This relation, $M^TAM = B$ where $M$ is invertible, is called congruence 
- A matrix representing $f$ is congruent to another matrix iff it also represents $f$ under some basis.
## Symmetric And Anti-Symmetric Bilinear forms
- A bilinear form $f(v, u)$ is symmetric iff $f(v, u) = f(u, v)$
- for any given basis $w$ $f$ is symmetric iff $[f]_w$ is symmetric
- A bilinear form $f(v, u)$ is symmetric iff $f(v, u) = -f(u, v)$
- For any given basis $w$, $f$ is antisymmetric iff $[f]_w$ is antisymmetric ($M^t = -M$)
- If $1+1\neq0$, Every bilinear form is the sum of a symmetric and an anti-symmetric bilinear forms, $\frac{f(u, v) + f(v, u)}{2} + \frac{f(u, v) - f(v, u)}{2}$
- $f$ is antisymmetric iff $f(v,v) = 0$ for all $v \in V$

## Rank
As the rank of conjugate matrices is the same, you can define $\rho(f) = \text{rank} [f]_w$ for some basis $w$.
## Diagonalization
- Every symmetric bilinear form is diagonalizable, according to [[Matrix Conjugate#Diagonalization]].