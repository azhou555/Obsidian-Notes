#Bits #Hardware #Memory-Diagrams #Binary #Compiling 
## Practice Exam 1A Notes
- When swapping two strings, you can no longer use a temp String value like in Java
	- Instead, go through each index of the strings and individually swap them one at a time
	- Works best when they have the same length
- Don't forget the header files when compiling code
- Remember that each time you make an edit to the file, you have to rerun gcc and then run the new file
- Recall that malloc'd objects are stored in the heap, everything else is in the stack
- When you declare a pointer, it doesn't have any memory allocated to it yet->it just sits there
## Other Notes
### Bits & Context
- Every C or whatever other language file is actually encoded in bits(0's and 1's)
- Context is what allows us to turn the bits into a readable file(English characters)
- Without context, binary is just numbers, there is no default interpretation as to what numbers mean
- ASCII is the conversion system used to convert binary into chars
- Individual statements in C files are translated into low-level instructions and packaged in an executable object program, referred to as executable object files
- The process looks something like this:
	1. Source Program(hello.c)
		1. Preprocessor(cpp)
	2. Modified Source Program(hello.i)
		1. Compiler(cc1)
	3. Assembly Program(hello.s)
		1. Assembler(as)
	4. Relocatable object programs, binary(hello.o)
		1. Linker(ld)
	5. Executable object program, binary(hello)
- gcc is one such compiler, and the one that we use during class(produces /a.out)
- All of the above processes are produced by a single line:
`gcc -o hello hello.c`
### Common Hardware Organization
![[Hardware Layout.png]]
Important things to note:
- Buses carry binary bits back and forth between different components of the system
- I/O devices(input output) are the connection between the computer system and the external world(connections to a mouse and/or keyboard, display, disk)
- Main memory stores RAM
- Arithmetic logic unity(ALU) does the calculations
- Processor executes instructions
	- Note that the processor only has a limited number of most basic functions to perform its tasks: 
		1. Load: copy a byte from main memory into a register
		2. Store: copy a byte from a register to the main memory
		3. Operate: copy contents of two register bytes to ALU, performs some arithmetic/logic operation using the two bits and copies the result into a register
		4. Jump: Extract a word from instructions and copy into program counter(PC)
- Once the executable object program has been created, it can be run by simply typing `./hello` or even just `hello`. From there, the CPU will copy the instructions over into the main memory, and then start executing instructions
## Numbers and Binary
### Unsigned vs. Signed
- As mentioned before, binary bits in isolation have no meaning until they are given context
- Unsigned numbers are the standard representation of binary where the conversion is simply adding up the powers($1100 = 2^3+2^2+0+0 = 12$)
- On the other hand, signed numbers can be used to represent both positive and negative integers
## Memory Diagrams
Note that even if a local variable has not technically been defined yet at a certain position, the compiler knows that it is coming and will allocate the memory for it. 

## General Tips
Unlike in Java, arrays in C don't really exist as a standalone thing, but rather as a pointer of sorts. As a result, when you create a local array in a frame on the stack, the second the frame finishes its set of instructions and is popped off, the array loses its functionality -> the memory addresses it used to occupy have been deallocated. The first index of the array will remain since that is the value associated with the returned pointer, but everything else is gone. A simple fix is using malloc to allocate memory for the array in the heap rather than the stack, where it won't be deallocated after the function finishes running. 

Make sure to declare any methods used in main() before main(), or else contain them in a separate file and `#include<header.h>` at the beginning. 