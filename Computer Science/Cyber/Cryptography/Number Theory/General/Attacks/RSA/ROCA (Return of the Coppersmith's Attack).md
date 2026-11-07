An attack on primes generated of the form $k \times M + ((e^a) \pmod{M})$
where $M$ is a primorial, and $a, k$ are random and small.
The attack is based on [[Coppersmith Method]].
Specifically, denote $p = kM + (e^a \% M)$ and $q = lM + (e^b \% M)$.
## Detection
$n \equiv e^{ab} \pmod{M}$.
This can easily be checked for using discrete logarithm, due to the order of $e$ modulo $M$ being relatively small (but not bruteforce-able).
## The Attack
First, we'll pick $M' | M$ and replace $M$ with $M'$, such that the order of $e$ modulo $M'$ is the smallest possible and $M'$ is large enough so coppersmith will still work.
The condition specifically is $\frac{kM}{M'} < n^{1/4}$. Because $n \approx (kM)^2$
The threshold is $M' > n^{1/4}$.
For picking the best $M'$, we'll notice that the order of $e$ modulo $\prod p_i$, is the $\text{lcm}$ of the order of $e$ modulo $p_i$.
So we'll iterate over the divisors of the order of $e$ modulo $M$ (new order candidates), and pick the smallest divisor such that the product of all primes $p$ such that the order of $e$ modulo $p$ is big enough.
After we picked a new $M'$, we can brute force the order of one of the primes, $p$, modulo $M'$.
Assuming we have a candidate $a$, the matching $k$ is a root of $p(x) = xM' + (e^a \% M')$ modulo $p$.
We'll use [[Coppersmith Method]] to solve this.
$x$ should be small enough so its possible (we chose such $M'$).
Then we'll just compute $p$ and factor $n$.
## Implementation
Already in `RsaCtfTool`
`RsaCtfTool --publickey key.pem --attack roca --private`
Alternative sage code (slower and mostly impractical):
```python

def best_Mp(primes, e, min_bits):
    ords = {p: ZZ(Mod(e, p).multiplicative_order()) for p in primes}
    L = lcm(ords.values())
    for D in sorted(divisors(L)):
        Mp = prod(p for p in primes if D % ords[p] == 0)
        if RR(Mp).log2() >= min_bits:
            return Mp, D
    return None
 
def roca(n, e, primorial_order):
    n, e   = ZZ(n), ZZ(e)
    primes = primes_first_n(primorial_order)
    min_bits = ceil(n.nbits() * (0.5 - 0.20)) + 4
    Mp, order = best_Mp(primes, e, min_bits)
    max_k = isqrt(2*n) // Mp + 1 # bound for k
    beta = 0.49
    eps  = beta ** 2 / 4.001
 
    P = PolynomialRing(Zmod(n), 'x')
    x = P.gen()
    Minv = inverse_mod(Mp, n)
    c = ZZ(1)
    for a in range(order):
        for r in (x + c*Minv).small_roots(X=max_k, beta=beta,epsilon=eps):
            p = gcd(n, ZZ(r)*Mp + c)
            if 1 < p < n:
                return p, n // p
        c = c * e % Mp
        if a % 1000 == 0:
            print(f"{a} of {order} iterations done")
    raise ValueError("Failed to factor N using ROCA attack")

```