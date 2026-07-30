https://en.wikipedia.org/wiki/Logjam_(computer_security)
An attack on Diffie-Hellman with reused small prime.
The idea is that the standard algorithm for discrete logarithm, number field sieve, has most of the computationally heavy part only depending on the prime.
It allows to precompute it once, and then do a not-so-heavy computation for each further communication.