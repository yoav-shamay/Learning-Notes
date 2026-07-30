Finds optimal basis for lattices with dimension 2.
Optimal means both vectors are the shortest possible (the first vector is the shortest one, the second vector is the shortest second-largest vector possible among all possible basises).
The first vector is always the shortest one created by the lattice (SVP).
#### Pseudo Code
```
while True:
	If ||v2|| < ||v1|| swap v1 and v2
	m = round((v1 * v2) / (v1 * v1)) (* = dot product)
	if m == 0 return v1, v2
	v2 -= m * v1
```
The idea is to each time reduce v2 "as much as possible" by v1, similar to the GCD algorithm.
We stop when the vectors are orthogonal.
The operations means reducing `v2` by as much as the projection of `v1` fits on it.
It can be proven to be optimal. 