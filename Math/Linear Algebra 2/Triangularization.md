## Properties of triangular matrices
- $T_n(F)$ - all upper triangular matrices. It's a linear (sub)space
Given $A \in T_n(F)$ where it's main diagonal is $a_{11},...,a_{nn}$
- $P_A(x) = (x-a_{11})...(x-a_{nn})$ (the characteristic polynomial)
- It's eigenvalues are $a_{11},...,a_{1n}$ and the amount of times a value appears is it algebraic multiplicity
- $A \in T_n(F) \iff A^{-1} \in T_n(F)$
## Triangularization
- $P^{-1}AP = M$, where $A \in T_n(F)$ is triangularization of $A$. $P$ is said to triangularize $A$
- Diagonalization is in particular triangularization
- $A$ is triangularizable iff the characteristic polynomial of $A$ decomposes to linear factors
- if the characteristic polynomial of $A$ is $(x-\lambda_1)^{k_1}...(x-\lambda_n)^{k_n}$ then the characteristic polynomial of $A^m$ is $(x-\lambda_1^m)^{k_1}...(x-\lambda_n^m)^{k_n}$ 
- $P$ triangularizes $A$ iff it triangularizes $A^{-1}$
- You can expand the field to be algebraically closed, and then every matrix can be triangularized.
## Triangularization of linear transformations
- A base $B$ where $[T]_B$ is triangular
- $T$ is triangularizable iff its characteristic polynomial decomposes to linear factors
- for every basis $B'$, $T$ is triangularizable iff $[T]_{B'}$ is triangularizable
- Define $T_A(v) = Av$, then if $[T_A]_B \in T_n(F)$ then the matrix that its columns are the vectors in $B$ triangularizes $A$.
- $[T]_B \in T_n(F) \iff [T^{-1}]_B \in T_n(F)$
## Connection between triangulation and invariant subspaces
T can be triangularized if and only if there's a subspace sequence
$$
V_1 \subset V_2 \subset ... \subset V_n = v
$$
where $V_i$ is T-preserved and $\dim{V_i} = i$.
In particular,  for $B = (v_1,...,v_n)$  where the sequence is $V_i = \text{Sp}\{v_1,...,v_i\}$
$[T]_B \in T_n(F)$ iff every $V_i$ is T-preserved.
## Algorithm
The idea is to build [[#Connection between triangulation and invariant subspaces]] in reverse order, and each time find a vector to form a basis.
We will find $V_1 \supset V_2 \supset ... \supset V_n$. Each time we will find $v_i \in V_i$, such that $v_i \notin V_{i+1}$ and the basis will be $B = (v_1,...,v_n)$.
We assume $T$ decomposes to linear factors as this is the requirement.
Denote $P_T(x) = (x-a_1)...(x-a_n)$
### Step 1
denote $V_1 = V, T_1 = T$. We will find an eigenvector of $a_1$ and denote it as $v_1$.
### Steps 2-n
We will find subspace $V_k$ of $V_{k-1}$ such that $\text{Sp}\{v_{k-1}\} \oplus V_k = V_{k-1}$. We can do it by completing $v_{k-1}$ to a basis.
We'll denote $T_k = (T_{V_k,\text{Sp}\{v_{k-1}\}}T_{k-1})|_{V_k} = (T_{V_k,\text{Sp}\{v_1,...,v_{k-1}\}}T)|_{V_k}$
It's satisfied $P_{T_k}(x) = (x-a_k)...(x-a_n)$
We'll find $v_k$ an eigenvector of $a_k$ in $T_k$.
