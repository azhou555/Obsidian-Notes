```
let add a b =
	a + b 
```
compile he file, and then in terminal you can do `add 10 200` and get a response of `int = 210`
Alternatively, you can define the function inside the terminal. 
`let add a b = a+b;;`
`#use` keyword
Go look up syntax for if else 
`rec` keyword for a recursive function
**Mutuary** recursive functions, f1 uses f2 and f2 uses f1. They depend on each other. The first one needs to use the `let` keyword, but the second one doesn't. 
`[]` empty list
`::` to add something to a list
`1::2::3::[];;`
All elements of a list must be the same type. 
`let l = [1:2:3];;`
`match`
```
let neg b = 
	match b with
	true->false
	|false->true
```
```
let bar lst = 
	match lst with 
	[]->[]
	|[h::t]->t
```
head is first value, everything else counts as tail
