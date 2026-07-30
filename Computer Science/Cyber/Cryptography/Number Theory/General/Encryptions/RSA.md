## Process
Two primes are chosen $p, q$
$n = pq$
$\lambda = (p-1)(q-1)\;\text{or}\;\text{lca}(p-1,q-1)$ (you need $a^\lambda \equiv 1 \pmod{n}$)
choose $e$ coprime to $\lambda$ (usually 65537)
$d = e^{-1}\mod\lambda$
Public key: $(n, e)$
Private key: $d$
Encryption: $ct = msg^d \mod n$
Decryption: $msg = ct^d \mod n$