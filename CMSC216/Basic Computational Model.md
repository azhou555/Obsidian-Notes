#Hardware #Compiling 
- C is low level language, computational model is more important and necessary when attempting to code with C
- "Von Kauffman" model in which a computer has 4 basic physical components

- CPU: can executes instructions
- CONTROL: CPU knows WHICH instruction to execute
- MEMORY: data is stored and can change
- Address cell and a value cell is oftentimes the setup
- Input/Output device such as a SCREEN(Optional)
- Sequence of instructions is called a program that changes MEMORY and SCREEN
- Instructions are computed line by line
- CPU has a small memory address that registers which instruction it is currently at, represented as binary code, and increments that each time it completes a line of instruction
- Memory cells have fixed ADDRESS number, but the content, or value, can be changed
- Random Access Memory(RAM) is the concept that the value in any memory cell can be retrieved fast using address
- SCREEN is empty unless explicitly printed by program
- Print stuff while debugging programs to visualize the values in MEMORY
- Java bytecode is similar to assembly language in that it is very low level and can be quickly converted to binary, whether by assemblers or Java interpreters
- Most languages will allow variables, which are symbolic names associated with memory cells
- Variable names are decided by programmer, whereas the compiler/interpreter will automatically translate it to the memory cell/address
### Basic C
- C programs require memory cell names to be declared with the type of data that they will hold, equal sign indicates that the result on the right will be stored in the cell named on the left
```
int x;
x = 42;
int y = 31;
int tmp = x + y;
```

- Compiler reads variable declarations to determine how many memory cells are needed to represent the variable

```
printf("%d %d\n",x,y) 
```
shows variable values on the screen as decimal integers

%d represents a variable value, the d indicates that it should be a decimal
```
#include <stdio.h>            // header that declares existence of functions such as printf

int main(int argc, char *argv[]) {

…

return 0;                  // return from main(): 0 indicates success

}
```

- Run gcc file_name to compile the code, and then ./compiler_name to run it

- Remember to recompile the file if changes are made, or else running the compiler file will represent the previous state of the file
- a.out is typically the standard name of the compiler file
- Can be changed by running `gcc -o new_compiler_name file_name`
- 