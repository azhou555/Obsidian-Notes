#Arrays #Pointers 
Arrays in C
- Continuous block of homogeneous data
- Automatically allocated by the compiler/runtime with a fixed size that has to be declared
- `int a[3]` for an array of length 3, containing ints, called a
- Refer to a single element via a[3] -> the 3rd element in the array
- Bare name arr is the memory address where the array starts, doesn't need an & or anything of the sort
- Think of it as a memory location, in this case a longer memory location that contains multiple things rather than a single one,  as is the case with a pointer
- `int a[5]; //random values`
- `int a[] = {2, 3, 4}`
- `int a[3] = {4, 5, 6}`
- Pointers and arrays are interchangeable, if a function calls for one, the other can also be passed in as well without issue
- Size of the array cannot be changed -> it is likely that there are already values before and after the memory location of the array, stuff can't really be inserted(same as Java)
- Fixed chunk, it is difficult to resize
	- May have to simply copy things over to a different location if it runs out of space
- 
Pointers in C
- Pointer arithmetic
	- `p++;`
	- Add 1 to an int* byte, points to the next int -> moves 4 bytes forward
	- Add 1 to a double* byte, points to next double, -> moves 8 bytes forward
- A pointer can be assigned to an array
- Can be dereferenced
- NULL pointer, allocates memory for a pointer but doesn't actually store any value inside
Alternatives to Pointer Arithmetic
- Avoid changing value of pointers
- Use array indexing instead(square braces)
However, it can still be useful for String manipulation, scanning things straight into a memory address