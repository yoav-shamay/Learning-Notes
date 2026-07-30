## Theorem
Given $T: V \rightarrow V$.
Assume $M_T$ decomposes to $k \geq 2$ pairwise coprime non constant monic polynomials:
$M_T(x) = M_1(x)...M_k(x)$
Denote $V_i = \ker M_i(T)$ and it has a basis $B_i$.
Then:
- $V_i$ is a non-trivial T-invariant subspace
- $V = V_1 \oplus ... \oplus V_k$
- $M_{T|_{V_i}}(x) = M_i(x)$
- The representing matrix of T over $B = B_1 \cup ... \cup B_k$ is the diagonal block matrix created from $A_1,...,A_k$ where $A_i = [T_{V_i}]_{B_i}$
## For single eigenvalue polynomial
An interesting case is where $M_T(x) = (x-\lambda_1)^{b_1}...(x-\lambda_k)^{b_k}$
Then we demote $M_i(x) = (x-\lambda_i)^{b_i}$
Denote $a_i = \dim V_i$.
Then we also get:
- $P_T(x) = (x-\lambda_1)^{a_1}...(x-\lambda_k)^{a_k}$
- $P_{T|V_i}(x) = (x-\lambda_i)^{a_i}$
## Corollaries
- For matrix $A$ where $M_A(x) = (x-\lambda_1)^{b_1}...(x-\lambda_k)^{b_k}$ and $P_A(x) = (x-\lambda_1)^{a_1}...(x-\lambda_k)^{a_k}$, $A$ is similar to the diagonal block matrix created from $A_1,...,A_k$ where $M_{A_i}(x) = (x-\lambda_i)^{b_i}$ and $P_{A_i}(x) = (x-\lambda_i)^{a_i}$.
- The opposite for the theorem: if $V = V_1 \oplus ... \oplus V_k$ where $V_i$ is a T-preserved subspace satisfying $M_{T|_{V_i}} = (x-\lambda_i)^{b_i}$ where all $\lambda_i$ are different, $V_i = \ker(T-\lambda I)^{b_i}$
- 