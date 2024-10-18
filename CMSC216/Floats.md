## Floats
1. Real numbers can be approximated
2. Doing so represents numbers in a different way than integer representations
Consider decimals(fixed points) and what they mean when calculating the value of a number(positive versus negative powers of whatever mod is being used)
How many bits should represent positive and which ones negative?
Instead of a fixed point, we have floating points where number of bits for positive and negative can move around. 
`printf("%.4e", x)` prints numbers in scientific notation, 3 past the decimal point. (1.2346e+02). Uses power of 10 and always includes one non-zero digit left of decimal place. All standard procedure. 
Fractional Part is also called Significand and Mantissa -> stuff right of the dot. 
IEEE 754 Floating Point Standard specifies 32-bit float and 64-bit double. 
1 bit for sign, 8/11 bits for exponent multiplier, 23/52 bits for fractional part/mantissa, 7.22/15.95 decimal digits of accuracy. 
Sign bit- 1 is negative, 0 is positive