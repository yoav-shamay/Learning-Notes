	## Definition
- Linear space on R or C
- Also called unitary space on C or Euclidean Space on R
- has inner multiplication - returns a complex number (or real if on R)
- denoted $(u,v)$
- $(a+b,c)=(a,c)+(b,c)$
- $(\lambda * a, b) = \lambda * (a, b)$
- $(b, a) = \overline{(a, b)}$
- $(a, a) \geq 0$ and $(a, a) = 0 \iff a = 0$  (always real due to previous property)
## Standard Inner Multiplications
- standard inner multiplication over $\mathbb{R}^n$ or $\mathbb{C}^n$ - $\sum_i a_i * \overline{b_i}$
- on matrices: $(A,B) = tr(\overline{B}A)$
- For $b > a$ the standard inner multiplication over $R[x]$ or $R_n[x]$ is $(f, g) = \int_a^b f(x)*g(x)dx$ 
## Simple Properties
- $(a, b + c) = (a, b) + (a, c)$
- $(a + b, c + d) = (a, c) + (a, d) + (b, c) + (b, d)$
- $(a, \lambda * b) = \overline{\lambda}(a, b)$
## Matrix Representation
- Over $R^n$, can be represented as a matrix M where $(a, b) = a^TMb$.
- In general, with base $B$, can be represented as $(a,b) = {[a]_B}^TM[b]_B$
- $M_{ij} = (B_i, B_j)$ (or $(e_i, e_j)$ on the first case).
## Norm and Orthogonality
- $||v|| = \sqrt{(v, v)}$ 
- On standard inner multiplication: distance from origin
- distance: $d(u, v) = ||u - v||$ 
- On standard inner multiplication: Euclidean distance
- $v$ and $u$ are orthogonal if $(v, u) = 0$, also denoted $v \perp u$ 
- On standard inner multiplication: if the lines from origin are perpendicular
- $v$ is orthogonal to a subspace $U$ if $v \perp u$ for every $u \in u$
- $U^\perp = \{v | v \perp U\}$
- $V = U \oplus U^\perp$ for finitely created $V$.
- Every vector $v$ can be uniquely represented as $v_1 + v_2, v_1 \in U, v_2 \in U^\perp$. $v_1$ is called the orthogonal projection of $v$ on $U$.
- On standard inner multiplication - projection on a line / plane.
- distance from subspace: $d(v, U) = d(v, v_1) = ||v - v_1|| = ||v_2||$.
- On standard inner multiplication - distance from a line / plane.
- If $v \perp u$ then $||v+u||^2 = ||v||^2 + ||u||^2$.
- On standard inner multiplication - Pythagorean theorem
- The norm of the orthogonal projection is less than (or equal to if its the same vector) the norm of the vector - from the previous statement and positivity of norm.
- Cauchy–Schwarz theorem (or inequality): $|(v, u)|^2 \leq ||v||^2||u||^2$. Equality iff v, u are linearly dependent.
## Orthonormal basis
- Orthonormal basis - every 2 vectors are orthogonal and the norm of every vector is 1
- Every vector space has an orthonormal basis, can be created using the Gram-Schmidt Process.
- Orthogonal basis can be turned to orthonormal by dividing every vector by its norm
- If B is orthonormal, $[v]_B = ((v, B_1), (v, B_2), ..., (v, B_n))$.
- If B is just orthogonal we need to divide by the norm squared: $[v]_B = (\frac{(v, B_1)}{||B_1||^2}, \frac{(v, B_2)}{||B_2||^2}, ..., \frac{(v, B_n)}{||B_n||^2})$
- if B is orthonormal basis of $U$ the orthogonal projection of $v$ on $U$ is $\sum_i (v, B_i)B_i$ (similar to $[v]_B$, but for vectors outside of $U$).
- Similarly if B is just orthogonal we divide by the norm squared: $\sum_i \frac{(v, B_i)B_i}{||B_i||^2}$.
- Orthogonal set without zero is always linearly independent, and therefore is basis if its size is the dimension.