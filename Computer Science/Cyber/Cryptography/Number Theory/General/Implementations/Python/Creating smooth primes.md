My own implementation:
TODO library?
```python
from Crypto.Util.number import getPrime, isPrime

def create_smooth_prime(bit_count, smooth_bound):
    cur_mul = 2
    used_primes = set()
    while cur_mul.bit_count() < bit_count - smooth_bound + 1:
        p = getPrime(smooth_bound)
        if p not in used_primes:
            cur_mul *= getPrime(smooth_bound)
            used_primes.add(p)
    while True:
        p = getPrime(smooth_bound)
        if p in used_primes:
            continue
        guess = cur_mul * p
        if isPrime(guess + 1):
            return guess + 1
```