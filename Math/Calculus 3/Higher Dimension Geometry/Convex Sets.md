A set $A \subseteq R^k$ is convex iff for each $x, y \in A$ and $0 < \lambda < 1$, $\lambda x + (1 - \lambda)y \in A$.

This differs from [[Affine Subspaces]] with the requirement $0 < \lambda < 1$.

For a given $x$,$y$ the set $\lambda x + (1 - \lambda)y$ is called the interval between $x$ and $y$ (if $0 < \lambda < 1$ the interval is open, if $0 \leq \lambda \leq 1$ the interval is closed).
## Examples of Convex Sets
- If $|A| \leq 1$, then $A$ is convex
- If $A_1, ..., A_k$ are convex then $A_1 \cap ... \cap A_k$ is convex.
- A box $I_1 \times ... \times I_k$ for $I_1, ..., I_k$ real intervals is convex.
- An open / closed ball is convex
Given $\varphi : R^k \to R$ affine, those sets are convex:
- $\{x \in R^k | \varphi(x) < \alpha \}$
- $\{x \in R^k | \varphi(x) \leq \alpha \}$
- $\{x \in R^k | \varphi(x) > \alpha \}$
- $\{x \in R^k | \varphi(x) \geq \alpha \}$