## Basic C Semantics
- Declaring and initializing values
- No boolean in C, 0 is false and every other value, negative or positive, is evaluated as true
- `if(6){ ...} ` would run without any issue
- Remember that malloc can be used to allocate memory for an array, not just for structs
- Always remember to free the components of a struct first before freeing the struct itself
- Dangling pointer is a pointer that points to an address that has already been freed
- Be able to convert between octal(0), decimal, hexadecimal(0x), binary(0b)
### Two's Complement
To get the two's complement in binary, invert bits and add 1. To get the actual decimal number, if significant bit is 1 we take the complementary binary value and make it negative. If significant bit is 0, it stays the same. 

**Critical**, remember that 1 byte is 8 bits, and can represent a total of $2^8$ or $256$ total values. Hence, an int can contains a total of $2^{32}$ different values, or $4294967296$. 
### Arrays & Pointers
Notice the similarities between arrays and pointers -> both are references to some data in memory. Brace indexing, doesn't track size of memory area used. 
Also note the differences. Arrays are exclusive to Global and Stack memory areas. Pointers can also be in the heap(`malloc()`). Pointers can also be dereferenced -> the location that they point to can be changed. Cannot be done with arrays. 
**Basic Swap Function**:
```
void swap_ptr(int *a, int *b){
	int tmp = *a;
	*a = *b;
	*b= tmp;
	return;
}
```
### Sizes
Compile time size is not necessarily the same as runtime size. For some things like fixed variables for function calls and stuff that goes on the stack, the compiler will generally be able to recognize how much memory is needed and allocate that amount. However, things that rely on user input or things that need to be added, the compiler will not be able to discern how much memory is needed and that is where malloc() comes into play. For example, with user input we can do something like `malloc(sizeof(char)*strlen(charArray))`
[[Data Types, Pointers, & Arrays#^8de1c6|List of Common Data Types]]
Remember that you can make good use of the strlen() function, takes in char array as a parameter. 
### Casting
Casting data types just about the same as in Java, (int) data converts data into type int. Naturally, there are also constraints that go along with this e.g. you can't convert a char array into an int. 
### Strings
You can still declare a String in C similar to in Java using "", but the syntax would look more like `char *str = "Hello World!\n";`
Terminate character arrays '\0' character to indicate end. In the above example with `*str`, although we didn't explicitly include a terminate character, the compiler automatically arranged it for us. 
When manually writing, reading, changing, etc. an array, be aware that you could end up erasing or overwriting ending character. Ending fairy! 🧚
### 4 Local Regions of Program Memory
1. **Stack**: Automatic, push/pop with function calls, local variables, function frames, so on
2. **Heap**: malloc & free, manual memory management & things can stay in scope even after local frame has been popped off -> refer to Practice Exam 1B Problem 3
3. **Global**: Variables outside of functions, static vars, think of #define
4. **Text**: Program instructions in binary, after a runnable file has been compiled and converted to "machine speak" then the set of instructions gets downloaded to the Text portion of program memory
Global and Text regions are typically fixed in size. Stack grows towards heap, the more things are on the stack the lower the memory address gets. Possibility of stack overflow where stack holds too much memory and things start to encroach on heap memory space. 
[[Logical Regions of Program Memory.png]]
### Structs
Heterogeneous groupings of data. [[Valgrind, Structs, & Malloc#^98bf80|Syntax]] 
Remember to be able to distinguish between when to use the arrow pointer syntax and when to use the `.`. Arrow `->` is when you are working with a pointer to the desired struct. `.`. is used when you have direct access to the struct itself. 
### Files
Remember that `fopen()` returns a `FILE *`. Check for `fh == 0`, which is indicative of failing to open the file. Always remember to `fclose(fh)` at the end to free up any memory occupied by the file handle. 
Aside from the [[Files, Control Structures, & Binary#^c3e992|common]] functions that you are already experienced in working with, there is 
`size_t fread(void *dest, size_t byte_size, size_t count, FILE *fh)`
which reads binary data from an open file handle. Reads byte_size$*$count bytes into buffer pointed to by `*dest`. Returns number of bytes read. 
and 
`size_t fwrite(void *src, size_t byte_size, size_t count, FILE *fh)` which writes binary data to an open file handle. Attempts to read byte_size$*$count bytes from buffer pointed to by `*src`. Returns number of bytes written. 