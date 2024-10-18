---
---
* To check for linearity, observe what things might make a transformation not linear and look for those.
* Matrices of different sizes cannot be added together.
* (**A**+**B**)2 = (A+B)(A+B)
* (AB)2 = ABAB != AABB
* A2 = AA
* If the number of non zero row vectors, or the number of vectors, does not match the dimension of T's co-domain, T cannot be a one-to-one transformation
	* T: R3\-> R4 but only 3 pivots = not one-to-one
	* The number of rows cannot exceed the number of columns, or else there cannot be a pivot in every row
* If T is 1 to 1:
	* The columns of A span the codomain(Rn)
	* Every row has a pivot position

![[MATH240/image.png]]![[image.1.png]]
In terms of transformation matrices, think of x as the vector with entries composing of scalar constants that are multiplied against the column vectors of A
