## Creating
```python
F = GF(2)
rows = [[0, 1], [1, 0]]
mat = Matrix(F, rows)
```
## Basic Operations
```python
mul = mat1 * mat2
exp = mat ** exponenent
inv = mat.inverse()
inv = mat ** -1
order = mat.multiplicative_order()
submat = mat.submatrix(topleft_row, topleft_col, nrows, ncols
transpose = mat.transpose()
rows_list = list(mat)
flattened = mat.list()
```
## Diagonalize
```python
P, D = mat.eigenmatrix_right()
assert P.inverse() * mat * P == D
```
## Jordan form
```python
J = mat.jordan_form()
J, P = mat.jordan_form(transformation=True)
assert P.inverse() * mat * P == J
```
## Kernel (solutions)
```python
kernel = mat.kernel()
kernel_basis = mat.kernel().basis()
```
## Characteristic polynomial and eigenvalues
```python
char_pol = mat.charpoly()
char_pol_factors = mat.charpoly().factors()
eigenvalues = mat.eigenvalues()
eigenvectors = mat.eigenvectors()
eigenspaces = mat.eigenspaces_right() #can take basis using .basis()
```
## Solving Linear System of Equations
```python
solutions = mat.solve_right(vec)
assert mat * solutions == vec
```