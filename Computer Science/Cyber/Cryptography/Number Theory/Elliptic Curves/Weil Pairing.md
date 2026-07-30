A pairing (bilinear form, changing addition to multiplication due to notation) between the points with order dividing $n$ to the $n$th roots of unity.
It has the following properties:
- $e_n(P + Q, R) = e_n(P, R) \times e_n(Q, R)$ (bilinear form)
- $e_n(P, Q + R) = e_n(P, Q) \times e_n(P, R)$ (bilinear form)
- $e_n(aP, bQ) = e_n(P, Q)^{ab}$ (bilinear form)
- $e_n(a, b) = e_n(b, a)^{-1}$
- $e_n(a, a) = 1$ (follows from previous property)
- $\forall Q\ e_n(P, Q) = 1 \iff P = O$
- $\forall P\ e_n(P, Q) = 1 \iff Q = O$

## On Finite Fields
If the field is $F_q$, and we run an $n$ Weil Pairing:
Define the "Embedding Degree" of the curve, $k$ as the smallest number such that $n | q^k - 1$.
This means there's a $n$th root of unity on $GF(q^k)$.
Then the output is a number on $GF(q^k)$.
Is only viable with small embedding degree.
## Implementation
Can be implemented using `P.weil_pairing(Q, n)` in sagemath.