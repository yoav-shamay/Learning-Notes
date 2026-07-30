Allows to check given $G,aG, bG$ whether a given point is $abG$ - the decision version of diffie hellman.
Works only on supersingular curves with a small embedding degree, as it's a requirement for the distortion maps.
See [[Distortion Maps]] for theory details.
The idea is that $e_n(aG, f(bG)) = e_n(G, f(G))^{ab} = e_n(abG, f(G))$.
So for a candidate point $P$, if $e_n(aG, f(bG)) = e_n(P, f(G))$ then $P$ is almost certainly $abG$.
This doesn't work with normal pairing without a distortion map as $e_n(G, G) = 1$ so this check will be useless and will be true for any multiple of $G$.