Distortion maps are endomorphisms that map a point $P$ to another point $f(P)$ such that $f(P)$ is linearly independent of $P$.
Using $e_n(P, f(Q))$ allows to use a pairing that doesn't have the limitation that $(P, P) = 1$.
Only exists on supersingular curves - on $GF(p)$ it means that their order is $p + 1$.
Also is only viable with small embedding degree.
## Example Application
Let's say we have $P, aP$, $a^2P$, $a^3P$ and we want to differentiate them.
We'll use the fact that $e_n(aP, a^2P) = e_n(P, P)^{a^3}=e_n(P,a^3P)$, and this is the only such pair.
However, normally it's useless, due to that $e_n(P, P) = 1$.
So we'll use $e_n(P, f(Q))$ instead of $e_n(P, Q)$.
This can also be used to [[Decision Diffie Hellman using Distortion maps|solve decision diffie hellman]].
## Finding Distortion Maps
Roots of unity can be found using `field.zeta(order)`
### Curves of form $y^2 = x^3 + ax$
In this case, if there's $i$ satisfying $i^2 = 1$
This map works: $f(x, y) = (-x, iy)$ .
If it doesn't exist we can use field expansion, and use the curve over $F_{p^2}$ instead of $F_p$.
### Curves of form $y^2 = x^3 + b$
In this case, if there's $a$ satisfying $a^3 = 1$
This map works: $f(x, y) = (ax, y)$
If it doesn't exist we can use field expansion, and use the curve over $F_{p^2}$ instead of $F_p$.