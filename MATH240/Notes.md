---
---
### Determinant Properties

Theorem: Let A, C be square nxn matrices

1. If a multiple of one row of A is added to another row to produce a matrix B, then det B = det A
2. If two rows are interchanged to produce B, then det B = -det A
3. If one row of A is multiplied by k to produce B, then det B = k det A
4. det (AT) = det(A)
5. det(AC) = det(A)\*det(C)
6. det(kA) = kndet(A)
7. det(A\-1) = 1/det(A)

Theorem: A is invertible if det(A) != 0
Cramer's rule: xi = det(Ai(**b**))/det(A) -> replace ith column of A with **b** and find the determinant
Let A be an invertible nxn matrix. For any b in Rn, the unique sol of Ax =b, xi = det(Ai(b)/det(A)
Ai(b) = (a1 ... ai-1 b ai+1 .... an)
Theorem:
Aij denotes the resulting matrix after deleting the ith row and jth column of A
A\-1 = 1/det(A) \* adj(A)
Cij is the (i, j) cofactor = (-1)i+jdet(Aij)
(adj A)ij = Cji
If A 2x2 (3x) matrix, the area(volume) of the parallelogram (Parallelepiped) defined by the columns of A is |det(A)|
The vectors bound together to form a parallelogram/Parallelepiped

### Set Properties

Prop: If H is a subspace of V, H is a vector space of V
Def: Subspace of H

1. **0** is in H
2. H is closed under addition
3. H is closed under scalar multiplication

Def: Kernel -> Ker(T) = {**x** in V s.t. T(**x**) = **0**}
Given that A is the associated matrix of transformation T:
Ker(A) = Nul(A)
Range(T) = Col(A)

### Dimension

if a vector V is spanned by a finite set, then V is said to be finite dimensional

* The dimension of V(dim v) is the number of the vectors in a basis for V
* dim({0}) = 0

Thm: Any linearly indep. set of exactly p elements in V is a basis for V
Any spanning set of exactly p elements in V i s a basis for V
Def. The rank of a mxn matrix A is the dimension of col A
rank A = # of pivot col
The nullity of A is the dimension of Nul A
nullity A = # of free variables
Thm: Let A be a mxn matrix , rank A+nullity A = n
dim(row A) = dim (col A)
R2 is not necessarily a subspace of R3, needs to contain origin
PC<-B = (\[b1\]C... \[bn\]C)
Every Ax = b has a least squares solution, but not every Ax=b has a unique least squares solution
