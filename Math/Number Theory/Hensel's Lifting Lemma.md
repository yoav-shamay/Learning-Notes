Given a polynomial $f(x) \in \mathbb{Z}[x]$ and $x$ such that $f(x) \equiv 0 \pmod {p^n}$,
Allows to find $x'$ satisfying $f(x') \equiv 0 \pmod{p^{n+1}}$ and $x' \equiv x \pmod{p^n}$.
Assuming $f'(x)$ is invertible modulo $p$, denote $t \equiv f'(x)^{-1} \pmod{p}$
Then $x' = x - f(x)t$.
If we take $t \equiv f'(x)^{-1} \pmod{p^n}$, we get $f(x') \equiv 0 \pmod{p^{2n}}$.
This can be used to find root to a polynomial in the [[p-adic numbers]].