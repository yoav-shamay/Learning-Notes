$A$ = matrix, $T$ = transformation
## Minimal polynomial of matrix
- All polynomials zeroed by $A$ is a linear space close to multiplication
- The minimum degree monic polynomial zeroing $A$ is called the minimal polynomial
- It exists and unique
- Denoted as $M_A(x)$
- $M_A(x)$ is still the minimal polynomial if you look at it as a matrix under a field expansion
- A matrix is diagonalizable **iff** its minimal polynomial is $(x-\lambda_1)...(x-\lambda_n)$ where $\lambda$ are the unique eigenvalues of the matrix.
- If $A$ and $B$ are similar then $M_A(x) = M_B(x)$
- The minimal polynomial divides every polynomial that is zeroed by $A$, in particular the characteristic polynomial
- $P_A(x) | M_A(x)^n$
- For irreducible $P(x)$, $P(x) | P_A(x) \iff P(x) | M_A(x)$
- The minimal polynomial has all eigenvalues as roots, even under field expansions
- If the characteristic polynomial decomposes to linear factors then so is the minimal polynomial, has the same components with leq (non-zero) exponents
- If the minimal polynomial decomposes to linear factors so does the characteristic polynomial
- $\dim \text{Sp}\{I_n,A,A^2,...\} = \deg M_A$
- The exponent of $(x - \lambda)$ in the minimal polynomial is the minimal $b$ satisfying $\rho (T-\lambda I)^b = \rho (T-\lambda I)^{b+1}$ (and it stays constant for all larger exponents).
## Minimal polynomial of linear transformation
- minimum degree polynomial that is zeroed by $T$
- $M_T(x) = M_{[T]_B}(x)$ for every basis $B$
- The exponent of $(x - \lambda)$ in the minimal polynomial is the minimal $b$ satisfying $\ker (T-\lambda I)^b = \ker (T-\lambda I)^{b+1}$ (and it stays constant for all larger exponents).
- $M_{T|_W}(x) | M_T(x)$