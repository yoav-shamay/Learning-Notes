Using [[sagemath]].
## Import
Accessing the object requires an additional import:
```python
from sage.modules.free_module_integer import IntegerLattice
```
## Initiating
```python
# Vectors do not have to be a basis, just a generating set
lat = IntegerLattice([[0, 1, 2, 3], [4, 5, 6, 7], ..., [0, 1, 1, 1]])
M = matrix(ZZ, [[0, 1, 2, 3], [4, 5, 6, 7], ..., [0, 1, 1, 1]])
lat = IntegerLattice(M)
```
## Getting reduced basis (LLL-reduced)
```python
basis = lat.reduced_basis
```
`basis` will be an array of vectors, with the first one being the shortest.
## Getting closest vector (CVP)
```python
C = lat.approximate_closest_vector(v) # non exact, uses LLL
C = lat.closest_vector(v) # exact, non polynomial (takes forever on lattices that arne't very very small)
```
## Converting an array to lattice vector
Used to do operations (like subtracting) from basis / cvp vectors.
```python
v = vector(ZZ, [0, 1, 2, 3])
v = vector(RR, [0.2, 1, 4.5, 3])
```
## Lattice Intersection
```python
intersection = lat.intersection(lat2)
```
TODO what object it is, what you can do with it, is it fast
## Getting transformation matrix (to reduced basis)
```python
M = Matrix(ZZ, [[0, 1, 2, 3], [4, 5, 6, 7], ..., [0, 1, 1, 1]]) # Does not have to be a basis, just a generating set
B, U = M.LLL(transformation=True)
# B - is the LLL reduced basis (can have zero rows)
# U - the transformation matrix
assert U * M == B
```
## Gaussian Heuristic
A really fast expected SVP approximation.
See [[Theory#Gaussian Heuristic]] for more details.
TODO where in sage