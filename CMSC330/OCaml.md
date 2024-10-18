###### Syntax
`x = 2` is an expression and will evaluate to true or false given that `x` is defined. 
###### Paradigm
A way of looking at something. 
- The way it executes
- Syntax
- Grammar
- Organization
- etc
##### Imperative vs Functional
Imperative: procedural, building blocks are procedures and statements
Functional: States the desires result, but not exactly a step-by-step programming flow
*Immutable*: States can't be modified after creation
- Modification creates a new state
- Think of changing the value of an element in a list
*Higher Order*: Functions are passed as arguments and/or returned as results
##### Static vs. Dynamic
Different times of type checking
Static: type-checking happens before program is run(OCaml)
Dynamic: type-checking happens at runtime, so variables can change their data type (Python)
##### Implicit Vs. Explicit
Implicit: type is assumed, programmer doesn't have to declare the type(OCaml)
Explicit: type must be explicitly typed(Java)
### OCaml
Bootstrapped language(Typed in its own language)
Has built in types including int, float, char, string, bool, and unit
Composite data types include tuples, lists, options, and variants
Arithmetic operations are NOT overloaded
Tuples: heterogeneous and can have different types and vary in length. 
Lists: homogeneous, only one type and can vary in length
Cons(`::`) vs. Append(`@`)
- `elem::rest_of_list`
	- `elem` is added as the head of `rest_of_list`
	- `elem` and `rest_of_list` must match type
	- Can be nested, as long as last element is a list
- `lst1 @ lst2`
	- `lst2` is appended to the end of `lst1`
Functions are expressions and have a type. 
All values have types
Records and variants are both user-defined types
- Records are used for description
- Variants are used for polymorphism
Currying: transformation that takes in multiple arguments as a sequence of single argument functions
``let f a b = a+b in let g = f 5 in g 5;; #Evaluates to 10``
Shadowing: If a variable within a scope has the same name as a variable in the outer scope, the outer variable is shadowed by the inner variable. 
``let x = 5 in let x = 6 in x = 4; #Evaluates to 6, x=5 is shadowed``
Side effects: any effect that modifies the outside world during the evaluation of an expression, rather than simply returning  a value. 
Everything has data types, all values are expressions but not all expressions are values. 
Variable types are determined by the operation or syntax of the expression. 
#### Generics
Can be anything, type is unknown. OCaml will automatically match it when in use, and will describe it as `'a`, `'b`, etc. 
#### Type Inference
OCaml will assume types using what has been given
- In order to make a function work, it will try to make all elements into a type that satisfies the requirements such that the code will compile
- `let foo x y z = if x+y > 10 then z else "hello"`
	- OCaml will set `x` and `y` as ints to make the condition work, and set `z` to type string so that `val foo : int -> int -> string -> string = <fun>`
### Recursive Functions on a List
**Addition of using pattern matching**
Find last element of a list:
```
let rec last lst =
	match lst with
	|[]->[]
	|[x]-> [x]
	|_::t -> last t
```
Length of list
```
let rec length lst = 
	match lst with
	|[]->0
	|[_::t]->1 + length t
```
Sum of int list
```
let rec sum lst = 
	match lst with 
	[]->0
	h::t->h+sum t
```
Check member
```
let rec member lst x = 
	match lst with
	|[] -> false
	|h::t -> h == x || member t x
```
Append
```
let rec append lst x =
	match lst with 
	|[] -> [x]
	|h::t->h::append t x
```
Insert x into sorted list
```
let rec insert lst x =
	match lst with
	|[]->[x]
	|h::t->if h > x then x::lst else h::insert t x
```
Sort(Insertion Sort)
```
let rec sort lst = 
	match lst with
	|[] -> []
	|h::t -> insert (sort t) h
```
In vs out of scope using `let` and `in`. 
Tuples -> an object
```
(1, 2, 3)
(2, "hello")
```
Writing an or function:
```
let or_alt p = 
	match p with 
	|(_,true) -> true
	|(true,_)->true
	|_ -> false
```
Lambda functions:
```
let add x y = x + y
(fun x -> x + 1) *(int -> int)*
(fun x->x+1) 10;; ---> int = 11
let g = fun x y -> x+y;;
g 10 20;; ---> int 200
```
#### Higher Order Functions (HOF)
Map
```
map f [a1::a2:;a3...an];; ---> [f a1; f a2; f a3; ...f an]
```
Structure preserving: applying map to a list preserves the fact that it is a list and the length of the list. Simply changes the type of life, the individual elements of the list. 
Fold
```
fold (a 'b -> 'a) acc [] ---> 'a'
```
List.fold_left and List.fold_right
#### Imperative OCaml
`*=`, `!`, and `ref`. 
#### Property Based Testing
Given a function, we can describe a property pertaining to the result of the function. 
For example, a function `append list elem`, we should have that 
``length(list) < length(append list elem)``. 
If we have a function `reverse list` , 
``length(reverse list) = length(list)``. 
The purpose of PBT is that we want to be able to test for any bugs 
### FSMs
5 element tuple: {Set of all states, set of starting states, set of ending states, set of transitions, alphabet}
Note that alphabet does not contain $\epsilon$ . 
#### DFA vs NFA
Deterministic: given a state and an input/transition, it is certain where our next state will be. Not the case for NFA. Cannot have multiple transitions with the same symbol starting from the same state. All DFAs are considered NFAs. 
NFA are easier to build. DFA are easier to work with/check for matching. 
Convert NFA to DFA. Convert DFA to regex. 
e-closure: Given a state, everywhere that can be reached using any amount of epsilon transitions from that state. 
move: Given state and symbol, what states can be reached. 
Go look at the algorithm for converting between an NFA to a DFA. 