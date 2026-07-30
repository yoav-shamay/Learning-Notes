## Theory
- Elemental row operations are multiplying by the elemental matrix from left
- Elemental column operations are matching by the elementary column matrix (transpose of the elemental row matrix) from right
- The elementary row / column matrix is given by doing the operation on the identity matrix.
- The order of row operations and column operations commute arbitrarily as long as the order of all row operations and all column operations is the same
- the operation $A \rightarrow E^tAT$ where $E$ is an elementary column matrix, is called elementary conjugate.
- The operation is doing a row operation and at the same time doing the operation on the matching columns.
- Equivalent to doing any one before the other, but doesn't actually matter, can do at once - as long as you notice that in operations of "add multiple of row to another row" you don't really add both but add the entire 2x2 created from them. when zeroing basically just adding one.
- A matrix can be converted to all conjugate matrices by a sequence of elementary conjugate operations.
## Algorithm
Remember that the matrix is symmetric.
It's basically Gaussian elimination but doing it at the same time on columns and because the matrix is symmetrical it actually works.
Note that "at same time" is equivalent to rows then columns or the opposite, due to them commuting.
Repeat until the matrix is diagonal:
### Case 1 - $\alpha_{1i} = 0$ for $i > 1$
Continue recursively on the submatrix without the first row and column (column is also zero due to being symmetric)
### Case 2 - $\alpha_{11} \neq 0$
Remember $\alpha_{1i} = \alpha_{i1}$
For every $i > 1$, do:
$$
R_i \rightarrow R_i - \frac{\alpha_{i1}}{\alpha_{11}}R_1, C_i \rightarrow C_i - \frac{\alpha_{1i}}{\alpha_{11}}C_1
$$
Now continue recursively as in case 1
### Case 3 - $\alpha_{11} = 0$
If there's $\alpha_{ii} \neq 0$, you can swap $R_1,R_i$ and $C_1,C_i$.
Also, there's a non-zero value in the row $\alpha_{1i}$  (otherwise it's case 1). 
Add $R_i$ to $R_1$ and $C_i$ to $C_1$, now we'll get $\alpha_{11} = 2\alpha_{1i} \neq 0$.
## Finding diagonalizing matrix
You can find $M^t$ by applying the row operations to the identity matrix on the side at the same time (similar to Gaussian elimination).
Then finding $M$ is easy.