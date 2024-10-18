#### Basics
Assembly x84 64
64 bit registers
`gcc -0g -S exchange.c` to turn exchange.c into an assembl file. 
#### Registers
Know what the different registers do. 
Argument Registers
1. %rdi
2. %rsi
3. %rdx
4. %rcx
5. %r8
6. %r9
Return value is always stored in %rax. 
Stack pointer is %rsp. 
Always remember to use the command size according to the register size, make them match up. 
q & %rax, l & %eax, w & %ax, b & al. Note that the naming convention differs. 
With %r10, it looks something like %r10, %r10d, %r10w, %r10b. 
Remember that data movement involving small registers will not overwrite higher bits in extended register. 
Moving data to low 32 bit regs will automatically zero high 32-bits
`movl   $0xAABBCCDD, %eax` will make the other 32 bits zero by default. 
`%rax` becomes `0x00000000AABBCCDD`
On the other hand, moving data to the smaller regs will not zero higher bits. 
`movw    $0xCCDD, %ax` could result in something like 
`0x111111111111CCDD` if `%rax` was originally `0x1111111111111111`. 
Remember that a `movl` instruction will ONLY move 4 bytes. It may zero higher bits if it is a register, but in memory it will only change the values of 4 bytes. The same applies to `movw` and `movb`. 
##### Callee versus Caller register
Caller save registers are restored after calling a function. In other words, the value is lost(aside from %rax). On the other hand, callee save registers must be restored before returning. 
When the caller save registers aren't enough, you can start to use the callee registers. Importantly, the callee save registers will also retain their value through function calls, similarly to values stored on the stack. In order to use callee save registers, you have to first push them onto the stack. Before returning the function, you have to then pop them. If you push a register onto the stack, be careful not to push it onto the stack again in an inner function. Not sure exactly what happens, but whatever values are stored/intended to be stored in there will likely be lost. 

#### Stack
Stack pointer is stored in %rsp
Whenever we want to put stuff on the stack, we first have to make space on the stack. Say we want to store a 4 bit int on the stack. 
`subq   $4, %rsp`. 
This creates 4 bytes for us to use. We can then `movl    $5, (%rsp)` to store int 5 on the stack. Use relative addressing for this, it is the easiest. 
```
subq    $8, %rsp
movl    $2, (%rsp)
movl    $11, 4(%rsp)
```
Anytime you want to call a function, the stack must always be aligned to 16 byte boundaries. Typically, the pointer to the previous stack address(whatever called this function) will take up 8 bytes. You will often see arbitrary `subq    $8, %rsp` in functions just to align the stack before making any function calls. 
Remember that anytime you subtract from the stack(change where it is pointing), you have to restore the address that `%rsp` is pointing to at the end of the function. For the above example, before returning I would do something like `addq    $8, %rsp`. 
### Function Calls
As mentioned above, anytime you want to call a function, the stack has to be aligned to 16 byte boundaries. Unlike Java and other languages where you can do something like 
`y = my_function(5, x);`
In assembly, you have to first store the function arguments in the corresponding registers:
`%rdi, %rsi, %rdx`, etc. Afterwards, when the function ends, the return value will be stored in `%rax`. Translated into:
```
movq    $5, %rdi
movq    %rcx, %rsi    # Assuming x is stored in %rcx
call    my_function
movq    %rax, %rdx    # Assuming y is stored in %rdx
```
### Floats
Probably won't run into, but know just in case. 
We have some basic floating point register movements such as `vmov`, as well as conversion such as `vcvts` and arithmetic. Basically, think of it as the same as standard assembly instructions but with a v in front and used with floats instead of our standard long, int, short, byte. 
`vmins`, `vmaxs`, and `sqrts`. 
Honestly just know that assembly can deal with floats, don't look too deeply into it. 
### GDB
```
layout asm
layout regs
stepi
nexti
print $rax # Prints value in $rax
x $r8 # Examine memoery at $r8
x/8d $r8 # Examines memory at $r8, but prints as 8 4 byte decimals
x/16d $rsp # Prints top 16 stack variables as ints
```
### More Commands
```
addX   
subX
imulX
andX
orX
xorX
salX
sarX
shlX
shrX
incX
decX
negX
notX
```
Note that shl and sal are pretty much the same. shr and sar are not the same however. 
sar preserves the sign bit in two's complement. 
`leaX`, load effective address. Use this when you want to store the memory address of something somewhere. 
### idivq
Division is pretty difficult. In order to perform division, you have to store the dividend(what you want to divide) in `%rax`. Make sure to sign extend the "a" register into a 64 bit register as necessary. 
```
cwtl    # 16 bit to 32 bit, %ax to %eax
cltq    # 32 bit to 64 bit, %eax to %rax
cqto    # 64 bit to 128 bit, runs over into %rdx
```
After performing the division, the quotient(result of division) is stored in %rax and the remainder in %rdx. 
### %rip
First rule of thumb: don't mess with it! However, you should know what it is, what it is pointing to, and its significance(Hint, control flow, instruction lines). 
`%rip` is referred to as the instruction pointer. As the name implies, it determines what line of assembly code is currently being ran and will also dictate what line will be read next, and next, and so on. 
%rip points to the next instruction line to be read. Can be manipulated. Changes itself on its own. Recognize it. 
### Flags
We have 3 main flags in assembly: 
1. FLAGS
	1. 16 bit
	2. Most important bits in first 16
2. EFLAGS
	1. 32 bit
	2. Name shown in gdb
3. RFLAGS
	1. 64 bit
	2. Not used normally
When we perform commands, the flags are automatically set as a result(example, `cmpX`). 
We can manipulate which lines are read and in which order using line pointers(?)`.ERROR: `  and `jmp` instructions. There are many different types of jumps. In a common situation such as 
```
if(x > 7){
	// Some code
}
// Further code
```
we can translate that into assembly:
```
cmpq    $7, %rax    # Assuming x is stored in %rax
jg      .EXECUTABLE_CODE

# Further code

.EXECUTABLE_CODE:
# Some code
```
As if statements get more confusing and you need more of them, it can get pretty hard to keep track of the flow of the lines. Try and be consistent in the way that you are laying them out, and make sure that the names make sense or else your code will be basically unreadable. 
Aside from the `cmpX` instruction, there is also the `testX` instruction. 
`testX` is similar to an and. You might see it in a line like
```
testq %rax, %rax
jz    .ZERO_CASE
```
You might also use it to execute a block of code like
```
if(x && y){
	// Some code
}
```
and turn it into
```
testq    %rax, %rdx    # Assume x is in %rax and y is in %rdx
jnz      .BOTH_TRUE

.BOTH_TRUE:
# Some code
```
There is an entire list of different types of jumps. Read through it later as necessary. 2
### objdump?
Disassembles binary, makes it more readable in theory. 
### Accessing Structs in Assembly
In Java, C, etc, we usually have some conception of data being tied together and given a name. In Java, this takes the form of a class, such as
```
public class Library{

}
```
In a non-OOP language such as C, we have structs instead. Again, we can define the layout of a struct, initialize one, give its values names, and so on. We have things such as 
`temp->temp_mode` which can fetch its attributes using its name. However, it gets more tricky when you want to do this in assembly. A large part of this is because assembly has no way to define a struct or a group of data. Instead, structs are represented simply as clumps of data that happen to be grouped together. When you have a pointer to a stack passed in as an argument, perhaps, it is pretty simple. 

```
typedef struct{
	short tenths_degrees;
	char temp_mode;
} temp_t
```
Note that the data for temp_t consists of a total of 3 bytes. 
Assume that a pointer to a temp_t is passed in as the first argument in %rdi. In order to access its values, you might do something like
```
movw    (%rdi), %ax    # tenths_degrees is now moved into %ax
movb    2(%rdi), %cl   # temp_mode is now moved into %cl
```
It is more difficult when you have the data of the struct itself packed into a register. In the below example, assume that a temp_t is passed directly as an argument instead of a pointer to it. 
```
movq    %rdi, %rax         # Move the struct value into %rax
andq    $0xFFFFFF, %rax    # Get rid of higher bits(unwanted)
movw    %ax, %dx           # temp.tenths_degrees in %dx
sarq    $16, %rax          # Shifting to access to temp_mode
movb    %al, %cl           # temp.temp_mode in %cl
```
When you have a packed struct, the 64bit register may not be enough. As a result, it may extend into other argument registers and even into the stack if necessary. 
Issue is, struct layouts and padding can change from algorithm to algorithm. If you are using someone else's code, be careful about how the values in the structs are stored so that you are getting the right values. 