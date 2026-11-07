Specifically in $\mathbb{R}^3$.
The cross product of $u, v$, denoted $u \times v$, is the unique vector satisfying for each $x \in \mathbb{R}^3$:
$\det{M(u, v, x)} = (u \times v)x$
Where $M(u, v, x)$ is the matrix whose rows are $u, v, x$.
Direct formula: $(u_2v_3 - u_3v_2, u_3v_1 - u_1v_3, u_1v_2 - u_2v_1)$.
It's a vector orthogonal to both $u$ and $v$, and its direction is determined by the right hand rule.
## Properties
- $v \times u = -(u \times v)$
- $(\alpha u + \beta v) \times w = \alpha(u \times w) + \beta(v \times w)$
- $w \times (\alpha u + \beta v) = \alpha(w \times u) + \beta(w \times v)$
- $(u \times v)w = u(v \times w)$
- $u \times v = 0$ iff $u, v$ are linearly dependent.
- $|u \times v|^2 + (uv)^2 = |u|^2 |v|^2$
- $|u \times v| = |u||v| \sin \alpha$ where $\alpha$ is the angel between the points of $u$, $0$ and $v$.
- $u \times v = w$ iff: $w$ is orthogonal to $u, v$, $\det{M(u,v,w) \geq 0}$ and $|w| = |u||v|\sin{\alpha}$.
- $|u \times v| \leq |u||v|$
- If $|u| = 1$, then $u \times (u \times v) = -v$
- $(u \times v) \times w = (uw)v - (vw)u$
- $(u \times v) \times w + (v \times w) \times u + (w \times u) \times v = 0$
- 