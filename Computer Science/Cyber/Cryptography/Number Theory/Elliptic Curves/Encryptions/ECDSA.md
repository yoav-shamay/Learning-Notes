Elliptic Curve Digital Signature Algorithm.
The parameters are a curve and a point $G$ (regardless of the key itself, can be used in multiple instances and usually a standard curve).
Denote the order of $G$ as $n$.
The private key is a secret number $d \in [1, n - 1]$.
The public key is $Q = d \times G$.
## Signing
Given a message $m$:
- produce a number $z$ from $m$, for example using a hash.
- Select a random $k \in [1, n - 1]$
- Compute $r = (k * G).x \mod{n}$
- Compute $s = k^{-1} * (z + r * d) \mod n$
Signature is $(r, s)$.
## Verification
Given a message $m$ and a signature $(r, s)$:
- Validate $r, s \in [1, n - 1]$
- Get $z$ in the same way as signing.
- Compute $w = s^{-1} \mod{n}$
- Compute $u_1 = (z \times w) \mod{n}$
- Compute $u_2 = (r \times w) \mod{n}$
- Compute $P = u_1 \times G + u_2 \times Q$
If $P.x \equiv r \mod{n}$ then the signature is valid.
## Proof
It works because:
$P = u_1G + u_2Q + u_1G + u_2dG + (u_1 + u_2d)G$
 $u_1 + u_2d = zw + rwd = w(z + rd) = s^{-1}(z + rd) = (k^{-1}(z + rd))^{-1}(z + rd) = k(z + rd)^{-1}(z + rd) = k$
 Therefor $P.x = kG.x \equiv r \mod{n}$.
 Because the order of $G$ is $n$ if $a \equiv b \mod{n}$ then $aG = bG$, so it's okay to use modulo $n$ math
## Breaking ECDSA
### Known K
If you know K, with some math you can sign anything you want by multiplying by k, adding the hash difference and dividing by K again.
If k is small you can brute force it and find private key from signature
If order of G is small you can also brute force k.
### Insecurely Generated K
https://blog.trailofbits.com/2020/06/11/ecdsa-handle-with-care/
TODO learn
### Reused K
TODO write