---
---
Def: An eigenvector of an nxn matrix A is a vector x s.t. Ax = lambda x for some scalar lambda
A scalar lambda is called an eigenvalue of A if there is a nontrivial sol. x to Ax = lambda x
Eigenspace = ker(A\*lambda\*x), consists of zero vector and all of the possible eigenvectors
The set of all sol. to (A-lambda\*I)x = 0 is called the eigenspace of A
If (A-lambda\*x) = 0 has a nontrivial sol, then lambda is an eigenvalue
TFAE:

* (A-lambda\*I)x = 0 has a non-trivial sol
* A-lambda\*I is non invertible
* det(A-lambda\*I) = 0

Def: let A, B be nxn matrices. A is similar to B if there exists an invertible matrix P s.t. P\-1AP = B (Q = P\-1, Q\-1BQ = A)
A -> P\-1AP similar transformation, A ~ B
If A is row equivalent to B, then A may not be similar to B
Thm: If nxn matrices A and B are similar, then they have the same characteristic polynomial and thus the same eigenvalue
Thm: An nxn matrix A is diagonalizable if and only if A has n linearly independent eigenectors. In fact, A=PDP\-1 if and only if the columns of P are linearly independent eigenvectors of If Rn has a basis of eigenvalues of A, then A is diagonizable
\[T(x)B\] = \[T\]B\[x\]B
Thm: Suppose A = PDP\-1, D -diagonal matrix . If B is a basis for Rn formed from the columns of P, then D = \[T\]B, where Tx = Ax
A ~ B if there exists invertible matrix P s.t. P\-1AP = B
PB1<-B2 = (PB2<-B1)\-1
