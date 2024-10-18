#Manual-Memory-Management #Memory  #Malloc
Segmentation Fault: attempting to access something in the memory that isn't in the scope of the file/whatever, basically just trying to read something that should not be read. Unpredictable results. 
malloc(nbytes) is used to allocate bytes in the memory
- Single arg -> number of bytes of memory
- Frequently used with sizeof() operator to determine how many bytes are needed -> sizeof() * number of bytes for each element
- returns a void* to bytes found or NULL if not enough space could be allocated
free() is used to release memory and operates the same way. 
- Can only be used on something that has been used with malloc()
- If something has already been freed and user attempts to free() it, an error will be created. 
**Manual Memory Management**
Ask for the number of bytes wanted, and then releasing the bytes later on. 
Typically, it is a better idea to use the stack to dynamically manage memory. 
However, there will be times where manual is better such as instances where the stack might be cleared but the data needs to be retained. 
Using malloc() and free() is an example of dynamic memory allocation. 
malloc() is good at allocating memory for things that might not be known until runtime -> the compiler wouldn't be able to predict how much memory to allocate. 
`sizeof(thing)` determines the size of an object at the compile time, not the run time. 
- Useful for malloc'ing things with a known size
- Not useful for sizes of arrays or strings -> the size of an array is unknown, will instead return the size of the pointer to the array
Every time malloc() allocates some memory, it allocates a little bit more in order to store data about the memory allocated that free() uses to free the data. 
Note that the return type of malloc() is a pointer to the memory address that it frees. 
```
int *arrptr = malloc(sizeof(int)*x);
```
### 4 Local Regions of Program Memory
1. Stack: automatic, with push/pop calls and frames!
2. Heap, malloc() and free()
3. Global, variables outside functions and static vars
4. Text: Program instructions in binary
Stack grows towards Heap, when there's a collision it's called stack overflow. 
Global and Text regions are typically fixed in size. 
May also have Logical Regions for humans to organize their programs. 
No physical differences for regions. 
[[Logical Regions of Program Memory.png]]
Valgrind
