#Bitwise-Operators #Debuggers #GDB #Endinaness
### Endinaness
Byte ordering in memory. 
Single bytes like ASCII characters are laid out sequentially in memory in increasing address
Multi byte entities require decisions on byte ordering
**Little Endian** - least significant byte early
**Big Endian** - Most significant byte early
With little endian, think of it as being stored backwards(?) smaller bits show up earlier in memory. 
Most modern machines use little endian by default, largely as a result of Intel choosing little endian. 
However, in network programming big endian is used instead. 
Processors have to be able to process and send in both little and big endian. 
### Arithmetic Logic
Arithmetic and Logic Unit(ALU) does integer ops in the machine, that includes multiplication and division done in binary. Although addition, subtraction, shifts, etc are typically 1 cycle long, multiplication is 3 cycles long and division is at least 30 cycles long
### Bitwise Operation
**Truthy** versus **falsey**
Bitwise operations happen bit to bit, think component-wise. 
Shifts -> moves the bits in a certain direction by $n$ positions/indices. 
Using shifts can multiply and divide by powers of 2
Compiler will automatically use shifts instead of standard division and multiplication if powers of 2 are involved
**Bit Masking**
