Described in http://hydra.azilian.net/Papers/Weak%20Curves%20in%20Elliptic%20Curve%20Cryptography.pdf
An attack on curves with Trace of Frobenius one, which means that they are of order $p$ (on the field is $\mathbb{Z}_p$).
This attack solves the discrete logarithm problem efficiently.
Denote the points as $P$ and $Q = kP$, we need to find $k$.
Denote the curve as $E(\mathbb{F}_p) : y^2 = x^3 + ax + b$
The attack consists of those steps:
1. Reduce the problem to DLP on a curve over $Q_p$
2. Further reduce the problem to DLP over additive $F_p$
3. DLP over additive $F_p$ is easy (division), solve it there.
## Reduction to $Q_p$
We'll map $a$ and $b$ to their corresponding p-adic integers to create the curve $E'(\mathbb{Q}_p)$.
In order to lift a point $P = (x, y)$ in E to E', we'll do the following:
We'll choose $x' = x$. If the lifting fails (the derivative is zero), we can choose any $x' \equiv x \pmod{p}$ instead.
In order to find $y'$, we'll start with $y' = y$ and use [[Hensel's Lifting Lemma]] to lift $y$ (as the y coordinate is a root for the elliptic curve polynomial).
We'll only lift the points once - we only care about them modulo $p^2$ for the attack.
We apply it on $P$, $Q$ to get $P'$, $Q'$.
The new $P'$ and $Q'$ might not fully satisfy $Q' = kP'$, however it satisfies $Q' \equiv kP' \pmod{p}$.
We'll denote $Q' = kP' + R$, where $R \equiv 0 \pmod{p}$.
Now we'll multiple the formula by $p$.
Because the original curve had order $p$, for every point $P$ in the new curve, $pP \equiv 0 \pmod{p}$.
So the new formula is $pQ' = kpP' + pR$.
$pR \equiv 0 \pmod{p^2}$, so now we got $pQ' \equiv k(pP') \pmod {p^2}$
And $pQ' \equiv pP' \equiv 0 \pmod{p}$.
## Reducing to DLP over additive $F_p$
There exists an homomorphism, called the p-adic logarithm map on elliptic curves, that maps between points on elliptic curves over $\mathbb{Q}_p$ that are close to the point in infinity (in this case that are 0 mod p)
Applying this finishes the reduction.
TODO some additional explanation on the logarithm.
## Implementation
TODO - maybe already implemented in sage