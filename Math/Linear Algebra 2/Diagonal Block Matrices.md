## Definition
$$
A = \begin{pmatrix}
A_1 \\
 & A_2 \\
 & & ... \\
 & & & A_m
\end{pmatrix}
$$
$A_i$ are all square matrices
The blanks are filled with zeros.
$A$ is called a diagonal block matrix. $A$ is said to be made out of the $m$ blocks $A_1,...,A_m$.
## Connection to linear transformations
Denote $V = V_1 \oplus ... \oplus V_m$
and $B_i$ a basis for $V_i$, and $k_i = \dim V_i$
Let $B = B_1 \cup ... \cup B_m$ be the ordered basis where $B_1$ comes first then $B_2$ and so on.
### From linear transformations
Given a linear transformation $T$, where every $B_i$ is $T$ preserved
Then $[T]_B$ is the diagonal block matrix made out of $A_1,...,A_m$, where $A_i$ is of size $k_i \times k_i$, and $A_i = [T|_{V_i}]_{B_i}$
### To linear transformations
The opposite is also true - if $[T]_B$ is the diagonal block matrix made out of $A_1,...,A_m$ 
where $A_i$ is of size $k_i \times k_i$ then $V_i$ is $T$ preserved and $[T|_{V_i}]_{B_i} = A_i$.
### On standard basis
Given $A$ a diagonal block matrix from $A_1,...,A_m$ and $E = (e_1,...,e_n)$ the standard basis.
Denote the size of $A_i$ as $k_i$.
Denote:
$$
\begin{matrix}
E_1 = (e_1,...,e_{k_1}) \\
E_2 = (E_{k_1 + 1},...,E_{k_1 + k_2}) \\
... \\
E_m = (E_{k_1 + ... + k_{m-1}},...,E_{k_1 + ... + k_{m-1} + k_m})
\end{matrix}
$$
And $V_i = \text{Sp}(E_i)$.
Then $F_n = V_1 \oplus ... \oplus V_m$.
So $V_i$ is $T_A$ preserved and $A_i = [T_A|_{V_i}]_{E_i}$

## Properties
For $A$ made out of $A_1,...,A_m$ and $B$ out of $B_1,...,B_m$ where $A_i$ and $B_i$ are the same size:
- $A + B$ is the diagonal block matrix made out of $A_1+B_1,...,A_m+B_m$
- $\mu A$ is the diagonal block matrix made out of $\mu A_1,...,\mu A_m$
- $AB$ is the diagonal block matrix made out of $A_1B_1,...,A_mB_m$
- $A^t$ is a diagonal block matrix made out of $A_1^t,...,A_m^t$
- $A$ is invertible iff $A_1,...,A_m$ are all invertible and $A^{-1}$ is the diagonal block matrix made out of $A_1^{-1},...,A_m^{-1}$.
- For polynomial $Q$, $Q(A)$ is the diagonal block matrix made out of $Q(A_1),...,Q(A_m)$
- The characteristic polynomial $P_A(x) = P_{A_1}(x) P_{A_2}(x) ... P_{A_m}(x)$
- The minimal polynomial $M_A(x) = \text{lcm}(M_{A_1}(x),...,M_{A_m}(x))$
- $|A| = |A_1|...|A_m|$
- The rank $\rho(A) = \rho(A_1) + ... + \rho(A_m)$
- Given a permutation $\sigma$, $A$ is similar to the diagonal matrix made from $A_{\sigma(1)},...,A_{\sigma(m)}$. Those matrices are said to be different in block order.
- 