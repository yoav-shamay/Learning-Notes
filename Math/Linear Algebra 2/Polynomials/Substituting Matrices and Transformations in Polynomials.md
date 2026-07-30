## Substituting matrices in polynomial
- As you will expect
- $(P + Q)(A) = P(A) + Q(A)$, $(P_1P_2)(A) = P_1(A)P_2(A)$, $(\alpha P(A)) =\alpha P(A)$
- $P_1(A)P_2(A) = P_2(A)P_1(A)$
- $B^{-1}P(A)B = P(B^{-1}AB)$
- $(P(A))^t = P(A^t)$
- A is said to zero $P(x)$ or $P(x)$ is zeroed by $A$ if $P(A) = 0$
- If $A$ and $B$ are similar then $P(A) = 0 \iff P(B) = 0$
- There's a polynomial $P$ zeroed by $A$ of degree at most $k$ iff $I_n, A, A^2, ..., A^k$ are linearly dependent
- $A_m \in \text{Sp}\{I_n, A, ..., A^{m-1}\}$ iff there's $P$ of degree $m$ zeroed by $A$
## Substituting linear transformation in polynomial
- As you will expect
- $[P(T)]_B = P([T]_B)$
- $(P + Q)(T) = P(T) + Q(T)$, $(P_1P_2)(T) = P_1(T)P_2(T)$, $(\alpha P(T)) =\alpha P(T)$
- $P_1(T)P_2(T) = P_2(T)P_1(T)$
- If $U$ is $T$-preserved then $U$ is $P(T)$ preserved and $P(T|_U)=P(T)|U$
- Given $W \subseteq V$ T-preserved space: $\ker(P(T|_W)) \subseteq \ker(P(T))$
- if $\ker(P(T)) \subseteq W$ then $\ker(P(T|_W)) = \ker(P(T))$
- T is said to zero $P(x)$ or $P(x)$ is zeroed by $T$ if $P(T) = 0$
- $P(T) = 0 \iff \exists B P([T]_B) = 0 \iff \forall B P([T]_B) = 0$
- $P(A) = 0 \iff P(T_A) = 0$
For $P_1, P_2$ coprime polynomials and $V_i = \ker P_i(T)$:
- $V_i$ are T-preserved
- $V_1 \cap V_2 = \{0\}$
- If $P(T) = 0$ then $V = V_1 \oplus V_2$
- 
## Cayley–Hamilton theorem
- $A$ zeros its characteristic polynomial
- $T$ zeros its characteristic polynomial