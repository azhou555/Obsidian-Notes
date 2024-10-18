#Valgrind #Structs #Malloc 
Valgrind:
https://valgrind.org/docs/manual/mc-manual.html#mc-manual.errormsgs
If you malloc something that will eventually be the return value, don't free it in the function:
free it at the end of the main function or whenever it is no longer needed. 
When you free something, you can never use it again. 
Structs:
Heterogeneous groupings of data
Each field of a struct can be a different type
Somewhat similar to Java's class/Object->has attributes
```
typedef struct{
  int an_int;
  double a_doub
  } thing_t
```

^98bf80

```
thing_t thing_a;
a_thing.a_int = 6;
```
 No privacy statement, everything is in scope
 Access elements using the dot notation. 
 Standard convention: has _t at end of name in order to be consistent
 ```
 thing_t b_thing {
 .an_int = 5;
 .a_doub = 19.2;
 };
```
Dynamically Allocated Structs can use the sizeof() operator to allocate memory. 
Structs can also have pointers to their own kind:
```
typedef struct node_struct{
char data[128];
struct node_struct *next;
} node_t;
```
Arrow Operator:
- Pointer to struct, want to work with a field
- Use arrow operator '->' for this
We use dot '.' when we are working with an actual struct. 
We use arrow '->' when we are working with a pointer to a struct