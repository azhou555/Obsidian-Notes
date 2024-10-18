---
---
For an orthogonal basis U for a subspace W of Rn, for any y in W:
y = c1u1+...+cnun
ci = y\*ui/(ui\*ui)
Otherwise, we can represent the projection of y onto W with:
y\_hat = c1u1+....+cnun with the same value for ci.
A set of vectors u1->p is orthornormal if ui\*uj is 1 if i=j and 0 if i != j
In other words, it is orthogonal and ||ui|| = i -> a set consisting of orthogonal, unit vectors.

Gram-Schmidt Process
basis -> orthogonal basis
With a basis {x1, x2.. xp} for space W,
v1 = x1
v2 = x2 - x2\*v1/(v1\*v1)\*v1
v3 = x3 - x3\*v1/(v1\*v1)\*v1-x3\*v2/(v2\*v2)\*v2

QR decomposition
A is mxn matrix with L.I. columns, A = QR.
Q is an mxn matrix whose columns form the orthogonal basis for col A
R is nxn upper triangular matrix with positive diagonal entries.
Use Gram-Schmidt Process to find Q and then use A = QR -> QTA = QTQR -> QTA = R
Mxn matrix U has orthogonal columns if UTU = I
