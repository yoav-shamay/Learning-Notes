The Galois Group of an extension $K / F$ is the set of automorphisms of $K$ over $F$, which means $f(x) = x$ for each $x \in F$.
The operation is composition.
It's denoted $G(K, F)$.
## Properties
- For each $\sigma \in G(K, F)$ and $g(x) \in F[x]$, then for each $x \in K$ such that $g(x) = 0$ then $g(\sigma(x)) = 0$.
- For $K / F$ where $|F| = q = p^k$, the Frobenius automorphism $\varphi(a) = a^q \in G(K, F)$, and it's fixed field is exactly $F$.
## Galois Group of a Splitting Field
If $K$ is the splitting field of $f(x) \in F[x]$.
This group is also called the Galois group of $f(x)$ over $F$.
- If $a, b \in F$ are roots of same irreducible factor of $f(x)$ in $F$, then there exists $\sigma \in G(K, F)$ such that $\sigma(a) = b$.
- $G(K, F)$ is isomorphic to a permutation group (which means it's some permutations, not necessarily $S_n$) over the roots of $f(x)$, and therefore its order divides $n!$.
## Galois Correspondence
Given a field extension $K / F$, denote $\tilde{L} = \{L | L \text{ is a field}, F \subseteq L \subseteq K\}$, and $\tilde{G} = \{G | G \text{ is a group}, G \subseteq G(K, F)\}$
Then we can define the following maps:
- $\varphi: \tilde{L} \to \tilde{G}$, such that $\varphi(L)$ is the subgroup of all automorphisms that keep $L$ (that $L$ is a subfield of their fixed field).
- $\psi: \tilde{G} \to \tilde{L}$, such that $\psi(H) = K^H$
In general, $H \subseteq \varphi(\psi(H))$