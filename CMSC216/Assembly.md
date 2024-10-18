## Assembly Language
The Machine Language of one professor is not understood by other processors. 
Most microprocessors are created to understand a binary machine language. 
We will study the x86-64 Assembly Language, which is popular among Intel/AMD chips with 64-bit word size. 
There are different types of syntax, remember to stick with the AT&T syntax and not the Intel syntax. Uses % to indicate registers rather than bare name. 
No sense of variables, variable names, that kind of stuff. Instead, value is directly stored in a register and it is dependent upon the coder to make sure that the right values are stored in the right register and then later retrieved properly. 
No loops, instead its system is what C's goto function is based off of: set positions in the code and then navigate there. 

Printing things in assembly is a lot of work, instead use gdb or something of the sort in order to see values. 
Blue text(movl, idivl, jmp, etc) are the base instructions that tell the CPU to perform some sort of operation. 
#### Registers
Registers are essentially just places in CPU memory that store some data, very fast access and can perform operations quickly
No loops, conditional whatevers, only jumps(goto)
Assembly can still be compiled using gcc(it produces assembly, runs it, so on)
Assembly is the lowest common denominator, it can be mixed in with other languages
Debuggers don't allow you to step backwards(oCaml?)
Instruction and register names dictate whether a 32 bit int or 64 bit long are being used
"General Purpose" registers have some sort of set purpose for which they are used for. 
%rax and %eax are return values, function args 1 through 6 are %rdi, %rsi, %rdx, %rcx, %r8, and %r9. 
r is for 64 bit(%rax) and e is for 32 bit(%eax)
Remember to always use the right naming convention. In a 64 bit system, just use r. Don't try to incorporate e. 
#### movX
Moving a 64 bit number into a 32 bit register will lop off the front half of the number
Data movement involving small registers may NOT overwrite higher bits in extended register. 
- Moving data to low 32-bit regs automatically zeros high 32-bits
- Moving data to other small regs does NOT alter high bits
Types of mov:
- movb: 1 byte
- movw: 2 bytes
- movl: 4 bytes
- movq: 8 bytes
Determines how many of the bytes are actually changed. 
#### addX
addX is similar to movX in that there are different sizes. 
`addX B, A # A = A+B`
First operand, or `B`, is left unchanged by the operation
#### leaX
leaX: Load Effective Address. 
- Memory addresses need to be loaded into registers, often done using leaX
- Similar to "address of" or & in C
#### idivX
Division is difficult. Specific rules are put in pace to make it easier. 
Dividend must be in the rax/eax/ax register. 
Sign extend to rdx/edx/dx register with cqto
idivX takes a single register argument which is the divisor. 
After completion, rax/eax/ax stores the quotient and rdx/edx/dx holds the remainder. 
## Control Flow in Assembly, Instruction Pointer
### %rip
%rip is a special register that points to the next assembly instruction to execute, hence the instruction pointer(points to the next pointer). Think of a linked list, performs current line, moves to next line, and then has a new next line. 
%rip automatically updates, do not perform arithmetic(subq, addq) with it. 
When there is a loop, %rip remembers the positioning and updates accordingly. 
### Stack & %rsp
%rsp is a pointer to the stack(refer to [[Logical Regions of Program Memory.png]]) 
Can use addq or subq to change where the stack pointer is pointing to in the stack 
`subq $8, %rsp` to make room for 8 bytes and then move stuff onto the stack. Remember to restore any changes to the %rsp pointer afterward. `addq $8, %rsp` at end of function. Remember Lab 7. Failing to align the stack pointer can still work, but it is liable to break the function and should just be ignored. 
#### Labels
`.LOOP`, `.END` are label examples that can be used with jump instructions to get somewhere. 
#### Conditional Jump
Used with labels to set up situations such as conditionals `(if x > y)`
#### Disassembling Binary
objdump on Unix, make binary files easier to read. 
`objdump -d prog > code.txt`
#### Comparison/Tests
cmpX/testX, does not alter things being compared and changes the EFLAGS register to reflect the results of the comparison/test
#### Logical And
Have two cmpX pointing to the same `.ELSE` label, if either of them match the non-desired criteria, then they will go to `.ELSE`. However, if they pass both compares, then there is no issue. 
#### call / ret with Return Address in Stack
When `call` is used, a pointer to the instruction is allocated on the stack before entering the function called. After function finishes, %rip goes back to where the pointer points. 
When `ret` is used, sets %rip to Return Address at top of stack(where function was called) and pop the return address off the stack.
#### Stack Alignment
%rsp must always be aligned with 16-byte boundaries when calling functions -> is divisible by 16. 
There may be arbitrary pushes or subtractions to %rsp in order to align %rsp to adhere to the boundaries. 
**ANY AND ALL MANUAL ADJUSTMENTS TO %rsp MUST BE REVERTED**. 
#### Register/Procedure Convention
To get extra Arguments, have to start using stack. Typically, assembly has 6 dedicated registers for arguments 1 through 6. Any extra must go on the stack(this is hard, won't have to do).
#### General Purpose Registers
Some registers are known as caller save registers, they restore after calling a function. Other registers are known as callee save registers, they restore before returning. 
#### Pushing and Popping to the Stack
When local variables or callee save registers are needed on the stack, can use push/pop
They are compound instructions that do multiple things, just compressed into one command
In actuality, they subq %rsp pointer and move a value onto the stack, or move something off the stack and addq %rsp. 
Anytime you push something onto the stack, you must also push it off the stack. 