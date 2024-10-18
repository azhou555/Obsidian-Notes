#Files #Control-Structures #Binary #Overflow #Underflow
Reading: Bryant/O'Hallaron Ch 2.1 - 2.3
`fopen(char *filename, "r"): ` ^c3e992
- Opens a file to read or write 'w'
- returns a file handle->FILE * if success
- returns NULL if unable to open file(don't fclose(NULL))
`fclose(FILE *FILEname):`
- Closes FILEname
- Free's memory associated with FILEname, make sure to do this every single time or valgrind won't like it
`fscanf(FILE *fh, char *format, addr1, addr2):`
- Reads data from file handle(fh) according to the *format string
- Stored the things read into the addresses
- Returns EOF if file is done
- Will keep going through empty space until it finds what its looking for
`fprintf(FILE *fh, char *format, arg1, arg2):`
- Prints data to open file handle according to format and provided arguments
void rewind(FILE *fh):
- Returns the open file handle to the beginning of the file
Files are typically stored in a format that is easier for the computer to read, but we view a version that has been adjusted for easy human reading. 
At the beginning of the file, it stores some data according to how it is formatted. 
Binary data files can be changed using two functions:
- size_t fread
	- Reads binary data from an open file handle, will return the number of bytes read
- size_t fwrite
	- Write binary data to open file handle, returns number of bytes written
Text formats are favored so that humans can understand, make edits, etc. as opposed to binary data files. 
Same control structures as java:
1. while(){}
2. for(){}
3. do{}while();
4. if(){}
5. if(){} else if(){} else{}
6. ternary operator
break:
- Breaks current loop, outer loop will still continue. 
continue:
- Continues onto next loop iteration, skips the rest of current loop
goto:
- Jumping around to different instructions
```
somewhere:
goto somewhere;
```
- Try to avoid goto when possible
- All loops are using goto in secret, they just make it easier to read and setup
switch()/case:
- He doesn't like it
### Binary & Numbers
Be able to convert between bases and how that all works
Common bases are decimal, hexadecimal, octal, and binary
C Prefixes:
- Decimal: None
- Binary: 0b
- Hexadecimal: 0x
- Octal: 0
ASCII, 7 bits per character: includes letters, upper, lower, and punctuation
### Two's Complement
Difference between signed and unsigned binary. 
Signed->first bit in binary becomes negative. 
Example: num = $1001 0101$
Unsigned = $2^7+2^4+2^2+2^0=149$
Signed = $-2^7+2^4+2^2+2^0 = -107$
Alternatively, we inverse the numbers(find the complement, $0$'s become $1$'s and $1$'s become $0$'s)and add 1. If the original number started with 1, we make it negative. If it started with 0, we make it positive. To convert a signed number back to a decimal, we just invert this process: Subtract 1, convert into binary and then find the complement. 
We can also think of the signed numbers as a loop. For 8 bytes, the first 128 values 00000000 to 01111111 becomes 0 to 127, whereas the values 10000000 to 11111111 becomes -128 to -1. 
Remember, numerical cycles! This comes up with #Overflow and #Underflow as well. 
num = $01101010 = 2^6+2^5+2^3+2^1 = 64+32+8+2 = 106\implies 107\implies -107\text{ unsigned}$
**Important**: positive signed numbers are equal to their unsigned counterparts. 
### Overflow and Underflow
Unsigned arithmetic addition/subtraction, numbers go either above 1111 1111 or below 0000 0000. Simple fix, arithmetic is considered in the context of a numeric ring. 11111111+00000001 = 00000000, 00000000 - 00000001 = 11111111. When arithmetic goes below 00000000, go back up to 11111111, and when arithmetic goes above 11111111, round back down to 00000000. 
Think of radians in a circle, we go from 0 to $\displaystyle \frac{\pi}{2}$ to $\displaystyle \pi$ to $\displaystyle \frac{3\pi}{2}$ and then to $2\pi$, but we don't actually go back above $2\pi$. Instead, we do trigonometry with $|2\pi|$ essentially. it is the same with overflow and underflow in unsigned binary, but instead we are working with $|100000000|$. 
### Chars and Codepoints
American standard ASCII uses 7 bit chars (8 bit is used to store context)to represent a total of 128 characters. Naturally, there are other languages out there with much more than 128 characters in their toolkit. UTF-8 uses 1-4 bytes per char instead of just 7 bits to represent many more characters. 