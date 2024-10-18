---
---
### Interfaces

* implements keyword
* Can have static variables, static methods, and default methods
* Methods defined in interface must be implemented if not already
* default methods are methods implemented in the interface that classes implementing the interface can use without further implementation
* public default void methodName(Parameters){...}
* Classes can implement multiple interfaces
* Polymorphism->Classes implementing an interface is a type of that interface(IsA)
* `public interace Iterable<T>{...}`

### Encapsulation & APIs

* Encapsulation is a procedure in Object oriented Programming that allows developers to change the code without affecting how code works, and still protect parts of their program
	* Data encapsulation -> Data structure has not been specified and can be changed
	* Procedural encapsulation -> Algorithm has not been specified and can be changed
* Classes and data exists, but we can hide parts of it and don't have to reveal all the code/attributes
* Collections.sort sorts an array. Although it uses the QuickSort algorithm, we don't actually know that it uses QuickSort. If the developers changed to a different sorting algorithm, we wouldn't notice as long as the end result is the same(Procedural encapsulation)

### Enums

* Java Class is a blueprint for an Object
	* Enums are classes that only have a fixed number of instances defined, enforced using a private constructor
	* Constructor can only be referenced within the class, thus more instances cannot be externally created
	* Classes -> Infinite many objects/instances, Enums -> limited number of instances

```
public enum Day{
    SUN(0), MON(1), TUES(2), WED(2), THU(2), FRI(2), SAT(1);
    public int hoursWorked;
    private Day(hoursWorked){
        this.hoursWorked = hoursWorked;
    }
    public int getHours(){
        return this.hoursWorked;
    }
}
```

* Note that the second line `SUN(0), MON(1), TUES(2) , etc;` are calls to the private constructor, defined by Day(hoursWorked). Essentially, `SUN(0)` defines a new instance of SUN with the value hoursWorked of 0, and if we call a getter such as `Day.SUN.getHours()` , it will return a value of 0.
* To access each enum object, use EnumName.ObjectName(Day.SUN)
* Order of definition matters
* .ordinal() returns index in which it was defined
	* Day.TUES.ordinal() = 2
* .values() returns array of all enum values
	* Can be used for iterating through enum values
* Can have instance variables, static variables, instance method implementation, static method implementation, private constructors, and fixed number of instances
	* No instance method prototypes

### Autoboxing and Autounboxing

* Involved with wrapper classes which represent primitives as objects-> int to Integer, double to Double, etc
* Integer a = 7; instead of Integer a = Integer.valueOf(7); <- Autoboxing
* System.out.println(a+14); <- Autounboxing

### Iterator

* Iterable<T> is an interface, any class implementing it can provide an iterator to go through its elements
* Only 1 method, public Iterator<T> iterator()
* T refers to the value of the collection/class that is being iterated
* Functional interface
* Iterator<E> interface defines methods for hasNext(), next(), & remove()
* Iterator<E> can be included as a static nested class
* Iterator object implements Iterator interface and allows user to go through collection/class

```
public class MyList<T> implements Iterable<T>{
    public iterator<T> iterator(){
        return new MyListIterator();
    }
}
public class myListIterator implements Iterator<>{
    public boolean hasNext();
    public T next();
    public void remove();
}
```

### Comparable and compareTo

* Comparable<T> interface: functional interface: has 1 method compareTo
* compareTo method, defines natural ordering for objects of type T
	* If we use Collections.sort(), it will use whatever ordering/metric of comparison to sort the objects
	* `public int compareTo(T other){...}`

```
Comparable<T> a = (other) -> {
    this.value-other.value;
}
```

### Comparators

* Allows to compare 2 objects of the same type using a metric.method
* Method defined in Comparator<T> interface, functional interface with one method:
	* `public int compare(T a, T b){...}`
* Allows to compare 2 objects without using the natural ordering process
* Implementable using a Anonymous inner class or lambda expression, or a different class if needed

```
Collections.sort(list, new Comparator<T> {
    public int compare(T a, T b){
        return a.value - b.value;
    }
};
Collections.sort(list, (a, b) -> {
    return a.value - b.value;
};
```

### Privacy Leaks / Mutability and Immutability

* Immutable objects are objects whose states cannot be changed after it is initialized -> Strings, int, primitives
* Mutable objects are objects whose states can be changed -> Objects, Arrays, ArrayLists
* A mutable object's state should only be changeable through its methods and ways that we want it to be able to be changed, such as setters
	* We do not want people to be able to change it in other ways

```
public class MutableObject{
    public String a;
    public String b;
    public MutableObject(String a, String b){
        this.a = a;
        this.b = b;
    }
}
public static void main(String[] args){
    MutableObject o = new MutableObject("a", "b");
    o.a = "c";    //We don't want this to be able to happen
}
```

* To fix the above example, we make variables a & b private, and then create setters such as `public void setA(String a) { this.a = a;}`
* Furthermore, if we reference a Mutable object in a constructor, if the original object is changed after the initialization of our class, the state of the class object will change as well. Thus, we want to create a new version of the original passed in value
* In getters, we also want to return a copy of the class object's instance variable so that it cannot be externally changed

```
public class MutableObject{
    private String[] a;
    public MutableObject(String[] a){
        this.a = a; //Bad, copy the array instead
    }
    public String getA(){
        return new String(a);
    }
}
public static void main(String[] args){
    String s = "hello";
    MutableObject o = new MutableObject(s);
    s = "bad";
    System.out.println(o.getA());
    String x = o.getA();
    x = "banana";
    System.out.println(x);
    System.out.println(o.getA());


```

### Inheritance

* Want to share implementation for methods/instance variables for multiple classes -> create an umbrella class that contains shared variables & methods
* extends keyword
* this refers to current object, whereas super refers to parent class of current object
* When constructing subclass, instance variables and methods are shared so super class needs to be initialized first \*THIS IS IMPORTANT
* Call to super is necessary -> ALWAYS CALL **super()** FIRST IN A CONSTRUCTOR

```
public class superClass{
    int a;
    int b;
    public superClass(int a, int b){
        this.a = a;
        this.b = b;
    }
}
public class subClass{
    int c;
    public subClass(int a, int b, int c){
        super(a, b);
        this.c = c;
    }
}
```
Abstract Classes

* Halfway between interfaces and inheritance
* Can have both abstract methods and normal methods
* Can have instance variables
* A class can only have one abstract class
* Non-abstract method can make calls to abstract methods in the abstract class
* Can have constructors, but an instance of the abstract class cannot be created
* `abstract public int x;` , abstract goes before
* `public  abstract class abstractClass`

### Exception Handling

* When exception is thrown, call stack will look for an exception handler and keep popping method after method until a handler is found, or there are no more methods and then everything will terminate
* Checked exceptions are checked during compile time, unchecked exceptions occur at runtime
	* Checked exceptions are usually out of user's bounds of responsibility, unchecked exceptions can be things like NullPointerException, coder's fault
* try-catch handling

```
try{
...
} catch (Throwable e){...}
```

* In this case, e is an exception object. The name can also be changed
	* e.printStackTrace();
* Can also declare that method throws exception, **throws** keyword
* `public static void getArea() throws FileNotFoundException{...}`

### Static Nested Class

* Just another class inside another class
* Privacy is NOT respected
* Helps with organization and making code look cleaner
* Example: writing an Iterator<T> within an Iterable<T> class

```
public class OuterClass{
    private int x;
    public static class NestedClass{
        //Methods, instance variables, etc
    }
}
```

* Inner class can reference the values of outer class

### Inner Class

* Similar to static nested class
* Needs instance of outer class to exist
* Privacy is not respected both ways

```
OuterClass x = new OuterClass();
OuterClass.InnerClass y = x.new InnerClass();
```

### Anonymous Inner Class

* Used to create an object on the fly, not going to be used again
* Object must implement or extend something

```
InterfaceName x = new InterfaceName(){...};
OR
InterfaceName<Generic> x = new InterfaceName<Generic>(){...};
```

```
Iterator<T> iterator(){
    return new Iterator<T>(){
        public boolean hasNext();
        public T next();
        public void remove();
    }
}
```

* Can be passed in as an object for a parameter, such as a Comparator

### Lambda Expressions

* Create a method on the fly that is not going to be reused
* Implemented interface has to be a functional interface

```
(a, b) -> {
    ...
}
```

* Java will recognize what "type" should be passed in as a parameter, and will automatically convert the lambda expression's method to fit the expected functional interface's method

```
Collections.sort(List list, Comparator<T> comparator){...}
makeTable(String s, BinaryFunction operator) {...}
public static void main(String[] args){
    makeTable(String s, (a, b) -> {
        return a*b;
    };
    Collections.sort(List list, (a, b) -> {
        return a.value - b.value;
    };
}
```

### Clone and Cloneable

* clone() method is inherited by all classes from Object class, which creates shallow copy of object
* Cloneable interface is a marker interface with no abstract methods or anything that simply indicates that there is a functional clone() method
* To implement clone(), superclass must be Object or must implement Cloneable
* Can throw CloneNotSupportedException if superclass is not Cloneable

```
public class Student implements Cloneable{
    private int id;
    private Address address; //Mutable
    ...
    @Override
    public Student clone() throws CloneNotSupportedException{
        Student copy = (Student)super.clone(); //Do for all immutable fields, calls a chain of calls to clone
        copy.address = address.clone(); //Do for all mutable fields, assumes Address has a functional clone() method
        return copy;
    }
}
```

* Will eventually need something to try and catch the CloneNotSupportedException since the clone() methods throws it

### GUI

* Processes and Threads
	* Processes creates/spawns threads to handle the work
	* Process handles execution of a program
		* Cannot interact with each other
	* Main thread, Garbage Collection Thread, Event Dispatching Thread
		* Threads can interact with each other, work on the CPU/execute code on the CPU
	* Basically, multiple threads are needed to do things simultaneously
* Event Driven Programming flow means that main thread initiates Event Dispatching Thread then dies, and then the Event Dispatching Thread will wait for events to happen and then react based on that
* Containers contain stuff, widget is just a thing that does something and is contained inside containers
* Layout Managers describe the layout of a container -> where widgets can go, where they are positioned
* Timer can be used to create delays
* paint() first creates the gui display, and repaint() redraws the gui with updated appearance

### O Notation

* Describes how long a program takes to run
* Represents how long code takes as a function of some sort
	* 1 second to process an element, n elements to process -> takes n seconds
		* f(n) = n
		* n is a variable that represents data size, a metric of some sort to represent the function
* Time isn't actually that simple, but we use O, o, and theta as bounds
* f(n) is O(g(n)) means that f is less than or in the same "ballpark" as g(n) -> f is faster or approximately equal to g
* f(n) is o(g(n)) -> f is strictly less than/faster than g
* f(n) is theta(g(n)) -> f is about the same as g
* We say that two functions are in the same "ballpark" or is approximately equal, if we can multiple one or the other function by a constant to make sure that that function is always less than or greater than the other function
	* Anything that is linear is approximately equal to each other & O(n), however they are also O(5n), O(n10000), blah blah blah
* Limit theorem: we can determine the relationships of time complexity between two functions with lim n->infinity f(n)/g(n)
	* If it diverges to infinity, g(n) is o(f(n))
	* If it converges to a non-zero constant, f(n) is theta(g(n))
	* If it converges to 0, f(n) is o(g(n))
	* Can use L'Hospital's almost every time since every algorithm probably diverges to infinity
