Given a set of linearly independent vectors $v_1,v_2,...,v_n$
The lattice created by them is the set of linear combination of them with integer coefficients.
## Volume of Fundamental Domain
The Volume of Fundamental Domain of a lattice is the absolute value of the determinant of the matrix with the basis of the lattice as its rows.
TODO - for non-square matrix
Intuitively, it represents the density of the lattice - the higher the value, the less dense the lattice is
## Basis
A basis is a set of vectors that every vector in the lattice can be represented in exactly one way as a linear combination of them with integer coefficients.
Alternatively, it's a set of vectors that span the lattice and the zero vector can be represented as a linear combination of them only when all coefficients are zero.
An optimal basis is a basis where the first vector is the shortest in the lattice, the second vector is the shortest second vector among all basises (even with a longer first vector), and so on.
- Every lattice has a basis
- Every lattice has a basis including the shortest vector
- Every lattice basis has the same element count, which is less than or equal to the dimension of the vectors in the lattice.
- Not every lattice has a perfect optimal basis - there exists a lattice for which for every basis with the shortest vector, the longest vector (or sum of lengths of all vectors) is longer than the longest vector (or sum of lengths of all vectors) of another basis.
- For 2D though there is always a perfect optimal basis, found by [[Gaussian Lattice Reduction]]
## Lattice Reduction
Reduce a basis to an optimal or a near-optimal basis, with vectors as short as possible, including the shortest possible vector as the first element in the basis.
Generally hard, polynomial up to 4d, but [[LLL]] is a good approximation.
## SVP and CVP
The following problems are hard (in the worst case) in lattices, and are used in encryptions.
- SVP: find the minimal (in magnitude) vector in lattice given its basis. polynomial in at most 4 dimensions.
- CVP - find the closest vector to a given one in the lattice given its basis
An approximation (or an optimal solution in some cases) can be found using [[LLL]].
Appear frequently in encryptions and approximation is very useful.
## Gaussian Heuristic
A heuristic used to approximate the expected value of the shortest vector in a random lattice.
For a nice (measurable) region $S \subseteq R^n$, the number of lattice points in $S$ is approximately $\text{Volume}(S) / \det{M}$
$\det{M}$ is the [[#Volume of Fundamental Domain|Volume of Fundamental Domain]] of the lattice ($M$ is a matrix with lattice basis as rows).
Applications:
- The shortest vector in the lattice is approximately $(\Gamma(n / 2 + 1)^{1/n} / \sqrt{\pi}) \cdot (\det{M})^{1/n}$
- For a large $n$ this is approximately $\sqrt{n/2\pi e} \cdot (\det{M})^{1/n}$
The shortest vector heuristic is useful to see if a short vector I found will actually be shorter than a random SVP (and if it's significant enough for approximations to work).