A number defined for every square matrix.
## Properties
- zero iff matrix is non invertible
- Of triangular matrix - product of the main diagonal.
## Impact by elementary operations
- swap two rows/columns - multiply by -1
- multiply row/col by $x$ - multiply by $x$
- Add to row a multiple of other row / same for cols - doesn't change
## Calculating
- Idea: gaussian elimination - to get a triangle, then multiply all diagonal (and take the impact of the operations into account)
- Can perform column operations in addition to row operations.
- If there's a row/column with all zero but 1, you can also remove the row+col of the non-zero cell, calculate the determinant, and multiply by the value of the non-zero cell. can help simplify, as there doesn't really need to be a proper triangle.