Used for factoring numbers where for a prime factor $p$, $p-1$ is smooth.
The idea is that $a^{k(p - 1)} \equiv 1 \mod{p}$ for $a > 0$
so we start with $a = 2$ and raise it to the power of every prime (or even every number) until the smoothness bound, and take gcd each time until we factor.
TODO explain better, including implementation.