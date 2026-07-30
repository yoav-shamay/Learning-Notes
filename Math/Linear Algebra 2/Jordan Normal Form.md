## Elementary Jordan Matrix
$$
J_n(\lambda) = 
\begin{pmatrix}
\lambda && 1 && 0 && ... && 0 && 0 && 0 \\
0 && \lambda && 1 && 0 && ... && 0 && 0 \\
0 && 0 && \lambda && 1 && 0 && ... && 0 \\
&& && && ... \\
0 && 0 && 0 && ... && 0 && 0 && \lambda
\end{pmatrix}
$$
It's called the elementary Jordan matrix of the eigenvalue $\lambda$. For $\lambda = 0$ it's called the elementary nilpotent Jordan matrix.
- $M_{J_n(\lambda)}(x) = P_{J_n(\lambda)}(x) = (x-\lambda)^n$
- $J_n(\lambda)$ is invertible iff $\lambda \neq 0$
- If $n > 1$ then $J_n(\lambda)$ isn't diagonalizable over any expansion field.
- $J_n(0)^n = 0$, $J_n(0)^{n-1} \neq 0$
- $J_n(0)^k$ is the matrix with the $k$ first columns as zero, and the $k+i$ column is $e_i$ for $i \geq 1$.
- $J_n(\lambda)^m = \sum_{k=0}^{\min(m, n - 1)} \binom{m}{k} \lambda^{m-k}J_n(0)^k$
- For $\lambda,m \neq 0$, $J_n(\lambda)^m$ is similar to $J_n(\lambda^m)$
## Connection between orbit and elementary Jordan nilpotent matrices
Given a linear space $V$, and $T \in \text{Hom}(V)$, and $v \in V$, denote $B = (T^{k-1}(v), T^{k-2}(v), ..., T(v), v)$:
1. If $v \in \ker T^k$ and $v \notin \ker T^{k - 1}$, Then $B$ is a basis for $\text{Orb}_T(v)$ and $[T|_{\text{Orb}_T(v)}]_B = J_k(0)$
2. If $\dim \text{Orb}_T(v) = k$ then $B$ is a basis for $\text{Orb}_T(v)$ and $v \notin \ker T^{k-1}$
3. If $T$ is nilpotent and $\dim \text{Orb}_T(v) = k$ then $v \in \ker T^k$ and $v \notin \ker T^{k-1}$.
## Jordan Matrix
A Jordan matrix is a diagonal block matrix made from blocks that are elementary Jordan matrices, in other words a diagonal block matrix made out of $J_{n_1}(\lambda_1)$,...,$J_{n_k}(\lambda_k)$
Note that some $\lambda$ can be equal.
For a Jordan matrix $J$ denote $\tau_m(J, \lambda)$ the amount of times $J_m(\lambda)$ appears as a block in $J$.
- $P_J(x) = (x-\lambda_1)^{n_1}...(x-\lambda_k)^{n_k}$
- The degree of $(x-\lambda)$ in $M_J(x)$ is the largest $n_i$ satisfying $\lambda_i = \lambda$.
- $\tau_m(J, \lambda) = \rho((J - \lambda I_n)^{m-1}) - 2\rho((J - \lambda I_n)^m) + \rho((J - \lambda I_n)^{m+1})$
## Jordan Form
- Every matrix (that its characteristic polynomial factors to linear factors) has a unique similar Jordan matrix (up to block order)
- Every transformation $T$ (that its characteristic polynomial factors to linear factors) has a basis $B$ satisfying that $[T]_B$ is a Jordan matrix, and the Jordan matrix is unique (up to block order).
- This Jordan Matrix is called the Jordan form
- For a transformation, $B$ is called a Jordan basis.
- The order of the largest Jordan block of $\lambda_i$ is the degree of $(x-\lambda_i)$ in the minimal polynomial
- The sum of the Jordan block sizes of $\lambda_i$ is the degree of $(x - \lambda_i)$ in the characteristic polynomial.
- The amount of Jordan blocks of $\lambda_i$ is the geometric multiplicity of $\lambda_i$.
- If the Jordan form of $A$ is $J$, $\tau_m(J, \lambda) = \rho((A - \lambda I)^{m-1}) - 2\rho((A - \lambda I)^m) + \rho((A - \lambda I)^{m+1})$
- If $P^{-1}AP = J$ , $P^{-1}(A-\lambda I)P = J - \lambda I$. This means the Jordan form of $A$ is equal to the (Jordan form of $A - \lambda I$) plus $\lambda I$ and the transformation matrix is the same.
## Finding Jordan Form of a Nilpotent Transformation
The idea is to find vectors $u_1, ..., u_l$ So $T = \text{Orb}(u_1) \oplus ... \oplus \text{Orb}(u_l)$.
Therefore, according to [[#Connection between orbit and elementary Jordan nilpotent matrices]], if we take a basis for each orbit (which is $T(v), T^2(v), ..., T^{k-1}(v)$ where $v \in \ker T^k \setminus \ker T^{k-1}$) and union them, we will get a Jordan basis of the transformation.

Denote $T^k = 0$.
Denote $V_i = \ker T^i$. ${0} \subset V_1 \subset ... \subset V_k = V$.
Denote $B_i$ a basis for $V_i$.

We will create 2 vector sequences: $D_k, D_{k-1},...,D_1$ and $E_k, E_{k-1}, ..., E_1$ (starting from $D_k$, $E_k$ and ending from $D_1$, $E_1$).
Our sequences will satisfy $E_i,D_i \subseteq V_i \setminus V_{i - 1}$, and that $D_i$ completes $B_{i-1}$ to a basis of $V_i$.
In step $i$ we will create $D$, $E$ of index $k - i + 1$.

The final result basis will be $\cup D_i = \cup_j \cup_{v \in E_j} B_T(v)$ where $B_T(v)$ is a basis for the orbit of $v$.
### Step 1
Let $E_{k}$ be a completion of $B_{k-1}$ to a basis of $V$, and $D_k = E_k$.
### Step $i$ ($2 \leq i \leq k$)
Denote $j = k - i + 1$ the current index we work on.
It holds that $T(D_{j+1}) \cup B_{j - 1}$ is a linear independent set in $V_j$ (and it's a disjoint union).
Let $E_j$ be a completion of $T(D_{j+1}) \cup B_{j - 1}$ to a basis of $V_j$.
It holds that $E_j \notin \text{Sp}(B_{j-1})$ and therefore $E_j \subseteq V_j \setminus V_{j-1}$.
Let $D_j = T(D_{j+1}) \cup E_j$
Therefore $D_j = T^{i - 1}(E_k) \cup ... \cup T(E_{j+1}) \cup E_j$.
## Finding Jordan Form of a General Matrix
First, use [[Primary Decomposition]] to make the matrix a diagonal block matrix that every block has a single eigenvalue, $\lambda_i$. 
Now for each block:
Find the Jordan form of $B-\lambda I$ for each block using [[#Finding Jordan Form of Nilpotent Matrix]].
The transformation matrix $P$ is the same, and the Jordan form will be $J + \lambda I$.
The total transformation matrix will be the diagonal block matrix made out of the transformation matrices of each block.
Now multiply both transformation matrices to get the total transformation matrix.