#Function-Call-Stack #Pointers #Memory
- Remember to do some backgrounding reading and familiarize with the language
- Try using MobaXTerm 23.5 version instead
### Function Call Stack
- Where functions store their local variables and data
- Caller function main() and Callee function swap()
- Caller pushes a stack frame onto the function call stack
- Caller tracks where it left off to resume later
- Caller copies values to Callee frame in the form of parameters
- Callee begins executing its first instruction
- Essentially, instructions are called, as a new function is called the necessary data is copied over into the new function. After new function finishes, it will pop off the call stack and all data inside the stack that hasn't been passed down to the previous frame is gone
	- Thus, the swap() function does not work since only the variables local to the swap() stack frame are swapped and not the ones in the main() function
- Stack frame
	- Variables are only local to the stack frame, not to other frames
- Top of the stack
	- Current frame that is being processed
	- CPU does things one at a time, meaning that only the instructions at the top of the stack are being run, everything else is just waiting for its turn
### Motivation for C
- Lower level language, above assembly but lower than Java and Python which cushion the programmer and hide some of the more technical aspects
### Von Neumann Machine
- Processing, basic arithmetic
- Memory, giant array of binary
- Control, instructions and order
- Input/Output, allows humans to interpret what the machine is doing and has special memory locations for keyboard, screen -> interaction
## C
- C allows direct use of memory cell addresses
- `&x`: Address of, memory address of variable x
- int `*a`: Pointer variable, a stores a memory address
- `*a`: Dereference, get/set the value pointed to by a
- To fix the swap function, pass in the address of x & y in the swap function, and then change the values inside the memory address
```swap(&x, &y)
void swap(int *a, int *b) // Here the * is a pointer to a & b
	int tmp = *a;
	 *a = *b; // Here * indicates that they are changing the values of a & b
	 *b = tmp;
	 return;
	 
```
- Pointers are typically 8 bytes, integers are 4 bytes
- Star/Asterisk `*` has 3 uses in C
	- Multiply numbers
	- Declare a pointer variable
		- `int *x;       // pointer to integer`
		- `int b = 4;`
		- `x = &b;       // point x at b`
		- `int **r;      // pointer to int pointer(s)`
	- Dereference a pointer variable
		- `int p = *x; //Declares an int p with the value of whatever x  is //pointing to`
		- `*p = y; // Sets the value that p is pointing to to y`
- scanf() beginner example
	- Reads something typed by user
	- Needs a memory address to store whatever is entered by the user
	- `int num = -1;`
	- `scanf("%d", &num)`
- Pointers allow user to access any data at any point in a program
- Allows high control of memory, but also more likely for mistakes to be made
- Remember that String as a data type doesn't actually exist in C. Instead, it has arrays of characters represented as codepoints in ASCII
10 - A
11 - B
12 - C
13 - D
14 - E
15 - F