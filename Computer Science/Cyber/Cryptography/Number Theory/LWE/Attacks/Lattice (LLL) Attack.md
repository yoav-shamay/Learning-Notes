Look at a group of plaintexts as a matrix (each row is the $x$ of a plaintext).
Then treat each column as a vector in a lattice, and take a look at the lattice span by them.
Then the vector of the results is a linear combination of the basis vectors (which means a vector in the lattice) plus some error terms (as that's how the matrix multiplication works).
This means that if you can solve the CVP (closest vector problem), you can solve LWE.
So using LLL-based approximate CVP is sometimes good enough (see [[Computer Science/Cyber/Cryptography/Number Theory/Lattices/Implementation#Getting closest vector (CVP)|here]] for implementation details).