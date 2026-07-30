Has a bunch of features, like excluding and counting: https://doc.sagemath.org/html/en/reference/sets/sage/sets/primes.html#sage.sets.primes.Primes
## Just all primes
```python
for p in Primes():
	print(p)
```
## Primes that are `a mod b`
```python
for p in Primes(modulus=4, classes=[3, 1]): # primes that are 1 or 3 mod 4
	print(p)
```
