#Data-Types #Pointers #Arrays
### Basics
Every programming language has:
- Comments
- Statements/Expressions
- Variable Types
- Assignment
- Basic Input/Output(printf() and scanf() for C)
- Function Declarations
- Conditionals(if-else)
- Iteration(loops)
- Aggregate data(arrays, structs, objects, etc)
- Library System
### Integral Data Types:
- char           1 byte
- short          2 bytes
- int              4 bytes
- long           8 bytes
Floating:
- float           4 bytes 6-7 sig digs
- double       8 bytes  15 sig digs
Pointers:
- pointer       4/8 bytes depending on 32 or 64 bit memory location
- array           Pointer to fixed location such as double [] or int [][], also gonna be 8 bytes
Consider that one byte is 8 bits -> can express 2^8 or 256 distinct values
Remember that it is asymmetric to represent negative numbers as well: 1 byte or a char can represent -128 to 127, 256 values including the 0. 
Note that there is no String type, but compilers can support pointers to arrays of character which will instead represent a String. However, you can still use something like %s in printf() to input a String. 
As such, C is not fit for large String processing. 
Additionally, there is technically, no "boolean", but any other type can represent a boolean since it is just a bit. Hence, any non-zero value represents true, whereas a 0 represents false. 
Recall that `*` references the value that a variable points at, but is also used to declare a pointer variable. 
Note that there is a void pointer `void *pointer` that can point to any type of value
However, it can no longer type check what it is pointing at, and will introduce risks. 
If the value that the void pointer is pointing to changes, make sure to adjust all associated values such as pointers pointing to where the void pointer is pointing. 
If a pointer thinks that what it is pointing to is a different type than it actually is, it will reference the wrong number of bytes and result in an incorrect value. 
`unsigned` removes the negative range of a type and instead increases the positive range: char goes from -128 : 127 to 0 : 255. 
There are also signed types with fixed widths that can specify properties such as int_fast8_t, which retrieves the fastest signed integer type with a width of 8. 
### Arrays
Continuous block of homogeneous (type) data. 
Automatically allocated by the compiler with a fixed size. 
[] syntax. 
Can index with something such as [3]
Bare name **arr** is the memory address where the array starts. 
`int a[3] = {10, 20, 30};`
Location of an array is not changeable, and their location reference is also not changeable whereas pointers can change their location reference and their location. 
The location of an array is also determined by the compiler. 
No concept of understanding its length: you cannot get the length of the array using something such as arr.length like in Java. 