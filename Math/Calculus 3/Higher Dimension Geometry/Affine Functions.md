A function $\varphi: R^k \to R^l$ is affine if it's the sum of a constant function and a linear function, $\varphi(x) = f(x) + b$ for a linear function $f$.
In other words, $\varphi = \tau_b \circ f$, where $\tau_b(x) = x + b$ (a translation).
## Properties
- A function $\varphi$ is affine iff $\varphi(x) - \varphi(0)$ is linear.
- $f$ is affine iff for each $x, y \in R^k$ and $\alpha, \beta \in R$ such that $\alpha + \beta = 1$, $f(\alpha x + \beta y) = \alpha f(x) + \beta f(y)$
- If $f$, $g$ are affine then $fg$ is affine
- If $f$ is an affine invertible function then $f^{-1}$ is affine
- If $f$ is affine and $A \subseteq R^k$ is affine then $f(A)$ is affine
- If $f$ is affine and its image isn't $R^l$ then its image is a subset of an affine space of dimension $l - 1$.
- If $f$ is affine and $K$ is convex then $f(K)$ is convex
- $f$ is affine if $[f]_1, ..., [f]_l$ are affine.