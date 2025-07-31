## Intro to java programming, object oriented programming, data structure and algorithm, and elementary programming in java

### JDK or JRE
- JRE (Java Runtime) physically present installation that provides the environment to only run the Java program
- JDK (Java Development Kit) physically present, which includes JRE plus the development tools (such as compilers and debuggers), is needed for writing Java program
- JVM (Java Virtual Machine) is part of JRE which is abstract machine responsible for
	- Loading code
	- Verifies code
	- Linking code
	- Executing codes
- compile and debug java programs, you will need JDK

##  Java Programming Language
- Class based
	- Basic unit is class except for 8 primitives data types
- Mostly object-oriented
- Case sensitive
- Statement housed in blocks of {  }
- Statements end with ;
- Desktop applications begins execution from main()
- better memory management that C++

### Object-Oriented-Programming
- OOP attempts to model all problems situations as objects
- An object (or instance) belongs to a class
- a class is a blueprint definition containing attributes (or properties, or data members) and behaviors (or methods)

### Identifier, Variable, and Constant
- Identifier is basically a name given to a class, method or variable,
	- a place where data is stored, An identifier
		- cannot start with digit
		- cannot contain space
		- cannot be a java keyword
		- can only contain special characters of dollar sign and underscore
	- variable name, is the identifier for a computer memory space to store data
	- data value stored in the variable, can be changed
	- constant, represents data whose value cannot be changed (eg Pi) constants declared with the keyword final
![[Pasted image 20250430001256.png]]


#### Declaring Variables
- variables has to be declared before it can be used to store data (or assigned with a value)
- can only be declared once within the same scope
- can be declared again under a different scope of code but it will be treated as a different variable
- int a; 
  int b; 
  int c; // the above 3 lines can be combined as int a, b, c; 
  float d;
 String e; 
 char f; 
 boolean g;

#### Declaring and initialising Constant
- Constant is a value that cannot be changed after assigning it
- naming convention is capitalized letters and underscore
- is defined with final
- the final modifier makes the value fixed
- final double MAX_WIDTH = 432.78;
- static and final, the static modifier makes it available without loading any instance of the class in which it is defined

#### Literals
- fixed values found in a program

#### Operators
- 5 categories of operators
	- Assignment : =, +=, -=, *=, /=, %=
	- Arithmetic:  +, -, *,  /, ++, --
	- Comparison/Relational: >, <, =, =\=, !=
	- Boolean: !, &&, ||, ^
	- Integer Bit-wise: >>, <<, |, &, >>>

#### Character Type and String Type
- Character is enclosed by single quote ''
- String value is enclosed by double quote ""
- string is not a primitive type. it is a class

##### Character type and operations
- character is stored as a sequence of 0s and 1s (binary)
- mapping a character to binary is called encoding
- java supports Unicode, 16-bit encoding scheme (0x0000 -- 0xFFFF)
- hence it is valid to code with \u (for 2-byte)
- Unicode also includes ASCII, 8-bit encoding scheme for commonly used characters (u\0000 to u\007F for first 128 values)

### String Class
- String is not a primitive type, String is a class
- String object can be created by **new** keyword or from a **literal**
- String literal -- a series of alphanumeric enclosed in double quotes
- whenever Java encounters a string literal for the first time, it creates a String object with the string literal. Subsequently, if the same value of this stored literal is required again, Java will not create any new copy but will reuse the stored copy

#### Comparing Strings
- == compares references, not content of strings
- equals() compares content of strings
- compareTo() compares two string content lexicographically

#### Conversion of String
- other variable types can be convert to String:
	- String.valueOf(23);
	- String.valuOf(56.78);
- String can also be converted to numeric, provided the original string contains only numeric and no alphabets, by the appropriate class and method

#### String is immutable
- Stings are immutable, meaning the values cannot be changed after they are created

### Getting inputs from console
- use scanner class
- System.in refers to console input from keyboard


### Implicit Casting
- data type is automatically casted/ converted and generally applies when a data type with a smaller range is assigned into a bigger data type

### Explicit Casting
- specific indication of data types within () and is needed when assigning value to variable of a type with smaller range


### Output Formatting
- System.out.printf("%d\n", 1234); 
  System.out.printf("%f\n", 12345.678f); 
  System.out.printf("%e\n", 12.345); 
  System.out.printf("%010d\n", 12);
  
- Output: 
  1234 
  12345.677734 
  1.234500e+01 
  0000000012
- ![[Pasted image 20250430003228.png]]


## Methods
- belong to a class
- collection of statements performing an operation inside a class
- has a method name
- contains code to be reused
- can be invoked (called) by using the method name
- primitive types are passed by value
- key difference between passed by value and reference : a duplicate copy of the data is created in a separate memory location when value is passed into the method


### Scope of variables
- scope of variable is determined by where the variable is being declared
- variables declared within a method are not visible ( not accessible) by codes outside the method
- variables declared in a loop are not visible by codes outside the loops

### Overloading Methods
- Methods with same name but different signatures
- this kinds of methods are called overloading methods
- modifier or return value types need not be the same
- java compiler determines which method is used based on best matching method signature


## Math APIs and Arrays
### Arrays
- Linear and static
- stores a group of like-typed item under one variable name
- each item is called element
- stores data in consecutive memory location
- storage memory is dynamically allocated but size cannot be changed once initialised
- array size must be specified by int or short value
- size is fixed, cannot be changed once it is defined
- has positioning index, starting from 0
- is subclass of Object
- Supports randomly access for elements stored


## Class Object and DIP
### Class
- basic unit of OOP is class
- class have class name
- class has data fields (attributes or properties)
- class has methods
- class encapsulates both data fields and methods
	- data field vs method
		- Data field store data
		- Method contains statements and code to perform certain actions
- Classes provided by JDK
	- Scanner
	- String
	- Math
### Class Constructor
- Constructor :
	- special kind of method
	- defined within the class itself
	- must have same name as class
	- does not have return type
	- called (invoked) automatically when object is created via new keyword
	- usually used to automate initialising of variables of the object
	- Overloading (Can call the class without a input for default value or call it with an input to set as the new value)
- this keyword
	- used tp differentiate internal attributes and incoming input parameters

#### Array of Objects
![[Pasted image 20250512131528.png]]

- sort using "Arrays.sort(array,comparator)"


### Object Reference
- object types variables are not primitive types of variables
- name of object variable represents the 'reference' to the object
- eg c2 =c1
	- c2 points to site storage of object c1
	- it does not copy from one object to another
	- object previously referenced by c2 is no longer accessible and is not garbage
- to clone object with all its fields, implement java.lang.Cloneable 

### String Class
- String is not a primitive data date but rather an object
- to modify original string object, use mutable classes like StringBuilder or StringBuffer


### Static Variable
- attached to a class
- shared by all instances (objects) of the class
- has only 'one copy' of the variable
- is declared with static keyword
- can be assessed by Class_name.variable_name (Circle.count)
- can also be assessed by object_name.variable_name (x.count, z.count)



### Static Method
- attached to a class (not any specific obejct)
- static modifier is added in front of a method
- can be assessed by Class_name.method_name
- can also be assessed by object_name.method_name
- can call only other static methods and static variables defined in the class
- if a non-static method and variable defined in the class, compiler will warn that all non-static variables or methods cannot be referenced from a static context


### Encapsulation
- 4 Characteristics commonly associated with OOP:
	- Encapsulation
	- Abstraction
	- Inheritance
	- Polymorphism
- Encapsulation is hiding implementation details of object within itself and only allow access to necessary data/method from outside the class
	- done by: employing various access modifiers
	- organising programs in packages


### Access Modifiers -- public vs private
- public - variable or method in class is accessible and available to ALL other objects in the entire program
- private - variable or method in class is accessible and available only within the class. Indirect access to private attributes in a class (from outside) can be achieved by using setter and getter methods provided by the class

### Package in java
- encapsulation can also be achieved by using packages
- package is used for better organising various class in a program
- with package, better accessibility control can be implemented
![[Pasted image 20250512133640.png]]


### Wrapper Class
- wrapper class in java provides mechanism to convert primitive into object and the other way round
- all classes of collection framework (ArrayList, LinkedList, Vector, HashSet, LinkedHashSet, TreeSet, PriorityQueue, ArrayDeque, etc.) deal with objects only
![[Pasted image 20250512134007.png]]


### Autoboxing
- conversion of primitive type into an object is known as autoboxing and unboxing


### Integer (wrapper class)
- Integer class wraps a value of primitive type int in an object
- integer object contains 1 field whose type is int
- also several methods to convert int to String 
![[Pasted image 20250512181018.png]]


### Dependency Inversion Principle (DIP)
- refers to coupling between different classes
- main idea is that high level classes should rely on abstraction rather than concrete implementation of lower classes
- 2 ways to implement DIP:
	- setter method
	- constructors



## Inheritance Polymorphism and ArrayLists

### Object Class
- many methods such as  toString() and equals() method
- parent class of all classes 

### Inheritance (extends)
- allows creation of new classes by reusing existing classes and adding additional attributes and methods

### Access Modifer
- if subclass is defined in different package from parent class, access to attributes or methods are limited to public or protected
![[Pasted image 20250512222348.png]]

### super()
- to be used in sub class's constructor
- call the no-arg constructor in immediate super class
- can happen automatically in sub class's constructor
- can also invoked explicitly
- when auto super call or explicit super call, it will activate the matching superclass constructor
- the match is determined by the number and data types of the arguments of the methods
![[Pasted image 20250512222737.png]]


### this()
- call the no-arg constructor of its own class
- used in constructor only
- if added,  must also be 1st statement
- if added, auto super() will be disabled

### Polymorphism
- object of subclass can be used by any code designed to work with an object of its superclass
- logical as subclas inherits everything from superclass
- subclass can do everything that is designed to be done by superclass
- 3allows same method name used in conjunction with different objects
- correct method chosen during running depends on type of object its associated with


### ArrayList
- resides within Java core libraries
- Linear and dynamic
- base on dynamic array (resizeable)
- can store different data types
- stores data in consecutive memory locations
- supports random access for elements (Index-based structure)
- < > in ArrayList declaration indicates that container is generic class (able to take in different data types or objects)]
- similar to other collections, arraylist does not take primitive types
- to store primitive types, respective wrapper classes are needed
- use add() to add new elements
- use remove(index) or remove(object) to remove elements
- use add(index, value) to insert new element 
- use get(index) to retrieve element
- use set(index, Object) to update element
- use sort(comparator) to sort elements by comparator
- use size() to find size of array
- use contains() to find if element is present
- use isEmpty() to check if list is empty

- ArrayList is not strongly typed 
- to create arraylist with mixed objects use:
``` ArrayList a1 = new ArrayList();```

### Generic Class
- arraylist is a generic class as it is able to handle different data types
``` ArrayList<String> a1 = new ArrayList<>();```
- will create a list of strings
``` ArrayList<Double> a2 = new ArrayList<>();```
- will create a list of doubles

### Custom Generic Class
- use < E > to represent generic class

![[Pasted image 20250512225555.png]]
![[Pasted image 20250512225602.png]]
![[Pasted image 20250512225607.png]]


## Exception Handling, Abstract Class and Interface

### Exception
- unexpected event caused by runtime errors
- may terminate abnormally without codes handling exceptions
- coded using try-catch or try-catch-finally structures
- try block will house the intended operation code
- execution of program will skip and jump to catch block is exception occurs during try block

### Arithmetic Exception

```
try{ 
	System.out.println (“Trying …"); 
	int x=30, y=0; 
	int z=x/y; 
	System.out.println ("Answer: "+ z); 
} 

catch(ArithmeticException e){ 
	System.out.println ("Cannot be divide a number by zero"); 
}
```

Output:
Trying … 
Cannot be divide a number by zero


### ArrayIndexOutOfBounds Exception

```
try{
	System.out.println("Trying ...");
	int x[] = new int[10];
	x[10] = 88;
	System.out.println("Done!");
}

catch (ArrayIndexOutOfBounds Exception e){
	System.out.println("No index in array");
}
```

Output:
Trying … 
No index in array


### NumberFormat Exception

```
try{
	System.out.println ("Trying …");
	double x = Double.parseDouble ("SP123");
	System.out.println (“x: "+ x);
}

catch(NumberFormatException e){
	System.out.println (“Wrong format");
}
```

Output: 
Trying … 
Wrong format


### Multiple Catch

```
try{
	int x[]=new int[7];
	x[4]=88/0;
	System.out.println("First print statement in try block");
}

catch(ArithmeticException e){
	System.out.println("Warning: ArithmeticException");
}

catch(ArrayIndexOutOfBoundsException e){
	System.out.println("Warning: ArrayIndexOutOfBoundsException");
}

catch(Exception e){
	System.out.println("Warning: Some Other exception");
}

System.out.println("Out of try-catch block...");
```

Output: 
Warning: ArithmeticException 
Out of try-catch block...


### try-catch-finally
- finally block will always run even if theres no exception thrown from try block

```
try{
	int x=888/0;
	System.out.println(x);
}

catch(ArithmeticException e){
	System.out.println("Number should not be divided by zero");
}

finally{
	System.out.println("This is finally block");
}

System.out.println("Out of try-catch-finally");

```

Output:
Number should not be divided by zero
This is finally block
Out of try-catch-finally


### throw
- keyword used inside a method
- needed to throw exception explicitly
- used in method signature
- used when method has some statements that can lead to exceptions

```
public static void validate(int age) {

	if(age<18) {
		throw new ArithmeticException ("Person is not eligible for competition");
	}
	else {
		System.out.println("Person is eligible for competition");
	}
}

public class Test {
	public static void main(String[] args) {
	
		try {
			validate (7);
		}
		catch(ArithmeticException e) {
			System.out.println(e.getMessage());
		} 
	}
}
```

### Checked/Uncheck Exceptions
- Unchecked Exceptions will not be checked by compiler during compile time
- examples of unchecked exceptions:
	- ArithmeticException
	- NullPointerException
	- ArrayIndexOutOfBoundsException
	- IllegalArgumentException
	- NumberFormatExcept

- examples of checked exceptions:
	- SQLException
	- IOException
	- ClassNotFoundException
	- InvocationTragetException


### Hierarchy of Exception Classes
![[Pasted image 20250519105002.png]]

### Try-with-resources

```
public class Test {
	public static void main(String[] args) {
	File myFile = new File("test.txt");
	
		try (Scanner scanner= new Scanner(myFile) {
			while (scanner.hasNext()) {
				System.out.println(scanner.nextLine());
			}
		}
		
		catch (FileNotFoundException e) {
			System.out.println(e.getMessage());
		}
	}
}
```


### Interface
- interfaces can have methods and data
- unlike class, it can only have constant data but not variables
- methods declared in an interface are usually abstract(only method signature, no logic, no implementation)
- it can also have static/default methods
- it can extend from another interface
- it cannot be instantiated
- used across unrelated classes ("capable of -doing" relations)
- can be used as return type for methods as long as the object returned implement the interface

example:

```
public interface Investment {    // Defining Interface
	double getInterest() ; 
	// No details of method here
	// NOT even empty body{};
	// It is to be implemented in
	// class(es) that inherit
	// (implements) the interface
}


public class SavingAccount implements Investment {    // Implementing Interface
	double balance;
	double iRate;
	public double getInterest() { // Details of method
		return (balance*iRate);
	}
}


public class Test {
	public static void main(String[] args) {   // Testing Interface
		SavingAccount a1 = new SavingAccount();
		a1.balance = 1000;
		a1.iRate = 0.005;
		System.out.println ( a1.getInterest() );
	}
}

```


#### UML
- interface is indicated in italics in UML notation
- implementation of interface is marked by dash-arrow leading from subclasses to interface
![[Pasted image 20250519105613.png]]


- when class has implements an interface, the class must provide implementation logic for all abstract methods specified in the interface
- essentially, it enforces "consistency" in software development

```
// This will thrown error as SavingAccount must provide logic for getInterest()
public interface Investment {
	double getInterest() ;
}

public class SavingAccount implements Investement {
	double balance;
	double iRate;
}


//Fix
public interface Investment {
	double getInterest() ;
}

public class Property implements Investment {
	double cost;
	double rentalReturn;
	double tax;
	
	public double getInterest() {
		return ( cost*rentalReturn - tax);
	}
}



```


#### interfaces with default methods
- classes implementing the interface can override the default method
```
public interface Investment {
	double getInterest() ; // abstract method
	
	default void display() {
		System.out.println("This is an investment.");
	}
} 
```


#### interface allows multiple inheritances
```
interface IncomeGain { double getInterest() ; }
interface CapitalGain { double getProfit() ; }

class SavingAccount implements IncomeGain, CapitalGain {

	double balance, investAmount;
	double iRate, ivProfit;
	
	public double getInterest() {
		return ( (balance- investAmount)*iRate );
	}
	
	public double getProfit() {
			return ( ivProfit );
	}
}
```


#### interface can extend other interfaces
```
interface Edible {
void serve();
}
interface Soluble {
void dissolve();
}
interface Seasoning extends Edible, Soluble {
void mix();
void marinate();
}

```

#### proper UML
</br>
![[Pasted image 20250519110233.png]]
</br>

### Abstract Class
- similar to normal class but it contains at least 1 abstract method
- abstract class can be extended using keyword "extends" (Interface can be implemented using keywords "implements")
- abstract class can provide both abstract and non-abstract methods
- it can contain no abstract methods
- however, a class with 1 or more abstract methods must be defined as an abstract class
- abstract class can have final, non-final, static and non-static variables (Interface has only static and final variables)
- Abstract class and interface both cannot be instantiated
- used in related classes ("is-a" relationships)

```
public abstract class BankAccount {
	protected String acctNum;
	protected double balance = 0, iRate;

	public abstract double getInterest();
	protected BankAccount(String a, double b) {
		acctNum = a;
		balance = b;
	}
}
```

#### Extends from abstract class

```
public class SavingAccount extends BankAccount {
	SavingAccount(String a, double b, double iRate ) {
		super (a,b);
		this.iRate = iRate;
	}
	
	public double getInterest() {
		return ( balance*iRate);
	}
}


public class currentAccount extends BankAccount {
	CurrentAccount(String a, double b) {
		super (a,b);
	}
	
	public double getInterest() {
		return ( 0.0);
	}
}
```


#### UML
</br>
![[Pasted image 20250519110700.png]]
</br>

## Java Collections Framework
- Supports 2 kinds of containers :
	- Collection - stores elements
	- Map - stores key-value pairs

### Collection Interface
- root interface in Java Collections Framework
- not directly implemented by any classes
- indirectly implemented via its sub-interfaces
	- List - store an ordered collection of elements
	- Queue - store elements in first-in-first-out manner
	- Set - store group of non-duplicate elements

### Simplified Collection Interface
</br>
![[Pasted image 20250702090016.png]]
</br>
### Concrete Classes in Collection
following are concrete classes of data structures in Java and they are direct subclasses of some other intermedia abstract classes:
- ArrayList, vector, LinkedList and Stack
- ArrayQueue and PriorityQueue
- HashSet, LinkedHashSet and TreeSet

</br>
![[Pasted image 20250702090214.png]]
</br>
![[Pasted image 20250702090223.png]]
</br>
![[Pasted image 20250702090320.png]]
</br>

### Classes implement List interface
- ArrayList - dynamic array (non-synchronised)
- Vector - legacy container, dynamic array (synchronised)
- Stack (sub class of Vector) - supports pop/peek/push operations
- LinkedList - dynamic and stores elements in non-consecutive manner in memory

#### ArrayList - concept
- resizable array
- elements stored according to natural order (order which they are added)
- elements stored in consecutive memory locations

#### Linked List - concept
- linked list has its elements spread out in memory in non-consecutive locations
- with a head pointing to 1st node and 1st node point to 2nd node and so one
- index is irrelevant

#### Main differences from array
![[Pasted image 20250702090818.png]]

### Chain of Nodes
- every node in a linked list contains:
	- Data
	- Reference to next node
</br>
![[Pasted image 20250702090904.png]]
</br>

- Last node in linked list contains
	- next = null

### Doubly Linked List - concept
- Every node in doubly linked list contains:
	- Data
	- Reference to next node and previous node
</br>
![[Pasted image 20250702091051.png]]
</br>

- Last node contains:
	- next = null
- First node contains:
	- previous = null

### LinkedList class in Java
- part of collection framework presents in java.util package
- linear data structure
- implemented using doubly linked list data structure
- can contain same or different object types
- efficient in removing/adding elements at both ends
- not efficient in removing/adding elements in between due to tracing (point-chasing) overhead
- does not need to move existing elements when removing/adding elements (advantage over ArrayList)
- out performs ArrayList in general

### Stack -concept
- linear data structure used to store collection of objects in Last-In-First-Out (LIFO) manner
- data can only be added/removed form the "top" of the stack
</br>
![[Pasted image 20250702091518.png]]
</br>
![[Pasted image 20250702091611.png]]
</br>
![[Pasted image 20250702091628.png]]
</br>


#### Stack from LinkedList
- simple stack can be implemented using concept of linked list


![[Pasted image 20250702091716.png]]



### Stack class in Java
- extends from Vector class
- internally is implemented using dynamic array (in contiguous memory locations) and not linked list
- many methods implemented in Java Stack class are very similar to that of ArrayList and LinkedList
- in generally reason for stack is for FILO nature


### Methods in List Classes

![[Pasted image 20250702091914.png]]


### Creating List Objects
```
ArrayList<Integer> a = new ArrayList<>();
Vector<Double> b = new Vector<>();
LinkedList<String> c = new LinkedList<>();
Stack<Circle> d = new Stack<>();

Collection<String> e = new ArrayList<>();
Collection<Integer> f = new LinkedList<>();
Collection<Member> g = new Vector<>()
Collection<Circle> h = new Stack<>();

List<String> i = new ArrayList<>();
List<Integer> j = new LinkedList<>();
List<Member> k = new Vector<>();
List<Circle> m = new Stack<>();

```

### Iterable Interface
- Collection is sub interface of iterable interface
</br>
![[Pasted image 20250702092402.png]]
</br>

### Iterator
- classic design pattern for navigating through a data structure
- useful methods: hasNext() and next()

```
ArrayList<String> a = new ArrayList<>();
a.add("Ang Mo Kio");
a.add("Dover");
a.add("Changi");

Iterator<String> it = a.iterator();
while(it.hasNext()){
	System.out.println(it.next().toUpperCase());
}


Output :
ANG MO KIO
DOVER
CHANGI
```


### Iterator and ListIterator Interface
- ListIterator extends from Iterator interface
- allows bidirectional traversal of the list
- List interface has methods that return Iterator and also ListIterator objects


![[Pasted image 20250702092730.png]]


### ListIterator
- extends from Iterator
- provides bidirectional traversal of list
- useful methods : hasNext(), next(), hasPrevious(), previous()

```
ArrayList<String> a = new ArrayList<>();
a.add("Ang Mo Kio");
a.add("Dover");
a.add("Changi");

ListIterator<String> it = a.listIterator();

while (it.hasNext()) {
	System.out.println(it.next().toUpperCase());
}

System.out.println("--");

while (it.hasPrevious()) {
	System.out.println(it.previous().toLowerCase());
}


Output:
ANG MO KIO
DOVER
CHANGI
-----
changi
dover
ang mo kio

```



### forEach
- inherited from interface Iterable

```
ArrayList<String> a = new ArrayList<>();
a.add("Ang Mo Kio");
a.add("Dover");
a.add("Changi");

a.forEach(e->System.out.println(e.toUpperCase()));   -> lambda expression


Output:
ANG MO KIO
DOVER
CHANGI
```

### Using Stack Class
- eg: create stack to store student objects from top
- use push() or add()
```
import java.util.*;

public static void main(String[] args){
	Stack<Student> a = new Stack<Student>();
	
	a.push(new Student("KK"));
	a.push(new Student("bobo"));
	a.add(new Student("tutu"));
	
	System.out.println(a);
}

class Student{
String name;
Student (String s) { name = s; }
@Override
public String toString() {return (name); }
}


Output:
[KK,bobo,tutu]
```

- Check top element (without removing)
```
public static void main(String[] args){
	Stack<Student> a = new Stack<Student>();
	
	a.push(new Student("KK"));
	a.push(new Student("bobo"));
	a.add(0,new Student("tutu"));
	
	System.out.println(a);
}

Output:
bobo
```

- Remove top element
```
public static void main(String[] args) {
	Stack<Student> a = new Stack<Student>();
	
	a.push(new Student("KK"));
	a.push(new Student("bobo"));
	a.add(0,new Student("tutu"));
	
	System.out.println(a.pop());
	System.out.println(a);
}


Output:
bobo
[tutu,kk]
```

- insert an item
```
public static void main(String[] args) {
	Stack<Student> a = new Stack<Student>();
	
	a.push(new Student("KK"));
	a.push(new Student("bobo"));
	a.add(0,new Student("tutu"));
	
	System.out.println(a);
}


Output:
[tutu,KK,bobo]
```

### Using ListIterator for Stack
```
public static void main(String[] args) {
	Stack<Student> a = new Stack<Student>();
	
	a.push(new Student("KK"));
	a.push(new Student("bobo"));
	a.add(0,new Student("tutu"));
	ListIterator it = a.listIterator();
	
	while(it.hasNext()){ System.out.println(it.next()); }
}

```

### Queue - concept
- First-In-First-Out Protocol
- Elements are inserted at end of the queue
- Elements are removed form front of queue
</br>
![[Pasted image 20250702094751.png]]
</br>

### DeQueue - "Double-ended" Queue
- Data can be inserted and removed from either end


![[Pasted image 20250702094835.png]]


### Queue in Java
- Queue in Java is an interface
- deque is child interface of queue

![[Pasted image 20250702094915.png]]


### ArrayDeque class
- implements Deque interface
- resizable-array that allows elements to be added/removed from both ends
- aka Array Deck
- has iterator
- no lListIterator
- has supporting methods to be used as a stack
- Methods:

![[Pasted image 20250702095045.png]]


### Using ArrayDeque Class
- Create Deque and add an item, use iterator to retrieve item
```
public static void main(String[] args){
	ArrayDeque<Student> a = new ArrayDeque<Student>();
	
	a.add(new Student("KK"));
	a.addFirst(new Student("bobo"));
	a.addLast(new Student("tutu"));
	
	System.out.println(a.size());
	
	Iterator<Student> it = a.iterator();
	while (it.hasNext()){ System.out.println(it.next().name); }
	
}


Output:
3
bobo
KK
tutu
```

### PriorityQueue Class
- implements Queue interface
- elements in priority queue are ordered according to natural ordering or by comparator provided at queue construction time
- Object elements stored must be comparable
- used when elements of queue are needed to be processed according to the priority
- using iterator or forEach will retrieve elements will not guarantee correct order
- use poll() instead to retrieve elements (will remove element)
- make copy by addAll()

### Using PriorityQueue Class
- create and add an item
- iterator and forEach will not guarantee correct order

```
public static void main(String[] args){
	PriorityQueue a = new PriorityQueue();
	
	a.add(82);
	a.add(11);
	a.add(35);
	
	Iterator it = a.iterator();
	while (it.hasNext()){ System.out.println(it.next()); }
}


Output:
11
82
35



public static void main(String[] args){
	PriorityQueue a = new PriorityQueue();
	
	a.add(82);
	a.add(11);
	a.add(35);
	
	a.forEach(e -> System.out.println(e));
}


Output:
11
82
35

```
- Use poll (read and remove) for correct order

```
public static void main(String[] args){
	PriorityQueue a = new PriorityQueue();
	
	a.add(82);
	a.add(11);
	a.add(35);
	
	while(!a.isEmpty()){
	System.out.println(a.poll())
	}
}


Output:
11
35
82


```

- Create PriorityQueue with comparator
```
public static void main(String[] args){
	PriorityQueue<Student> a = new PriorityQueue<Student>(new SortByGPA());
	
	a.add(newStudent("KK",3.8));
	a.add(newStudent("bobo",3.5));
	a.add(newStudent("tutu",2.9));
	
	PriorityQueue<Student> b = new PriorityQueue<Student>(new SortByGPA());
	b.addALL(a);
	while(!b.isEmpty()){
	System.out.println(a.poll().name)
	}
}

class SortByGPA implements Comparator<Student> {
	@Override
	public int compare(Student s1, Student s2) {
		return (Double.compare(s2.GPA, s1.GPA));
	}
}


Output:
KK
bobo
tutu
```

### Simplified - Set in Java
</br>
![[Pasted image 20250702101522.png]]
</br>

### HashSet in Java
- most common use
- implements set interface
- underlying data structure is key-value hash table
- does not allow duplicates
- does not guarantee order of elements
- (List always maintains the order)
- meaningless to access/remove elements by index

```
Set<String> schools = new HashSet<String>();
schools.add(“EEE”);
schools.add(“MAE”);
schools.add(“SMA”);
schools.add(“CLS”);
schools.add(“EEE”);

System.out.println (schools.size());
System.out.println (schools);
System.out.println (schools.isEmpty());
System.out.println (schools.contains(“MAD”));
```
#### HashSet - navigation methods
```
Set<String> schools = new HashSet<String>();
schools.add(“EEE”);
schools.add(“MAE”);
schools.add(“SMA”);
schools.add(“CLS”);

// Using for-loop
for (String school : schools) { System.out.println(school); }

//Using iterator
Iterator<String> schoolIterator = schools.iterator();
while (schoolIterator.hasNext()) {
	System.out.println(schoolIterator.next());
} 

```

### LinkedHashSet in Java
- maintains order in which elements are being added
- uses hash table and doubly-linked list to store and maintain elements
```
LinkedHashSet<Integer> a = new LinkedHashSet<>();

a.add(123);
a.add(45);
a.add(9);
a.add(3210);
a.add(9);
Iterator it = a.iterator();

while (it.hasNext()){
	System.out.println(it.next());
}
```

### TreeSet in Java
- similar to HashSet class and LinkedHashSet except that it auto sorts the elements
- implements self-balancing binary search tree
- elements must implement the comparable interface in order to be sorted
- to implement the itnerface, the object class must implement the compareTo() method, which returns 0, negative or positive integer values (for equal, smaller, greater than object)
- wrapper class Integer, Double, Byte, Short, Long, Float, Character, and String class all implement the Comparable interface
```
TreeSet<Integer> a = new TreeSet<>();

a.add(123);
a.add(45);
a.add(9);
a.add(3210);
a.add(9);

TreeSet<Integer> b = new TreeSet<>(a);

	b.forEach((x)->System.out.println(x));
}


Output:
9
45
123
3210

```

### Map Interface

![[Pasted image 20250702102554.png]]


### Concrete Classes in Map
- Map is a container that stores collection of key-value pairs
- similar to set, concrete classes of map are:
	- HashMap
		- store values by keys
		- no duplicates
		- allows 1 or more null
		- does not keep order which values are added
	- LinkedHashMap
		- Linked list implementation of HashMap
		- keeps order in which values are added
	- TreeMap
		- unique values
		- sorted according to key (in which the class must implement comparable interface)
- Unlike  Collection, the interfaces in Map Family do not provide iterator for traversal through the container

### HashMap
```
HashMap<String,String> a = new HashMap<>();


a.put("EEE","Electrical Electronics Engineering");
a.put("DE", "Digital Electronics");
a.put("new module", null);

a.forEach((abbr,fullname)->System.out.println(abbr +"==>" +fullname));

System.out.println(a.get("DE"));



Output:
DE==>Digital Electronics
new module==>null
EEE==>Electrical Electronics Engineering
Digital Electronics


```
- forEach - default method inherited from map interface

### TreeMap
```
TreeMap<Integer,String> a = new TreeMap<>();

a.put(7,"Electrical Electronics Engineering");
a.put(2, "Engineering Maths");
a.put(1, "Sports for Life");
a.put(1, "Engineering Maths");

a.forEach((id,fullname)->System.out.println(id +"==>" +fullname));


Output:
1==>Engineering Maths
2==>Engineering Math
7==>Electrical Electronics Engineering


```



## Recursive Programming

## Recursive Methods
- methods that calls itself

```
class TestRecursive {
	 public static void main(String[] args) {
		 shout();
	 }
	 
	// recursive method
	public static void shout() {
		System.out.println("AHHHHH! ");
		 shout();
	}
}

Output:
AHHHHH! 
AHHHHH! 
AHHHHH! 
： 
： 
(endless)
```


- recursive method must have a condition to stop the further calling of itself
```
class TestRecursive {
	 public static void main(String[] args) {
		 shout(5);
	 }
	 
	public static void shout(int x) {
		System.out.println(x + ".AHHHHH! ");
		if (x>1) shout(x-1);
	}
}


Output:
5.AHHHHH!
4.AHHHHH!
3.AHHHHH!
2.AHHHHH!
1.AHHHHH!
(stop)
```

### Recursive Nature
![[Pasted image 20250709004828.png]]
![[Pasted image 20250709004837.png]]

###  Factorial

```

class TestRecursive {
	public static void main(String[] args) {
	 System.out.println(fac(5));
	}
	
	public static int fac(int x) {
		if (x>1) {
		 return (x*fac(x-1));
		}
		return(1);
	}
}


Output:
120
```

```
Iteration Method

public static void main(String[] args) {
{
	int result = 1;
	for (int i=1; i<=5; i++) result *=i;
		System.out.println("result "+ result);
		
	return 0;
}



We want to achieve 5! = 1*2*3*4*5
– Start with result =1,
– In the for-loop, when i=1, result *= i yields  (1*1)
– Next loop, when i=2, result *= i yields (1*1*2)
– Next loop, when i=3, result *= i yields(1*1*2 *3)
– Next loop, when i=4, result *= i yields  (1*1*2 *3*4)
– Next loop, when i=5, result *= i yields  (1*1*2 *3*4*5)

```

### Recursive Programming
![[Pasted image 20250709005116.png]]
- Process of solving a problem by reducing it to smaller versions of itself
- General case for which the solution is obtained by calling the recursive function further
- base case for which the solution is obtained directly and stop the recursion
- all recursive algorithms can be implemented using iteration (conventional loop-structures)


### Iterative vs Recursive
|Iterative | Recursive|
|---|---|
|- Shorter Performance time|- Longer performance time|
|- More code| - Less code|
|- Usually start from "bottom" and iterate up  |- Start from "top"  and reduce to the bottom |
|- Must have condition to end loop, else infinite loop| - Must have base case to stop recursion, else infinite recursion|

### Considerations
- Recursion can take up significant resources
	- each call would cause a set of incomplete data and/or "unfinished" operations to be stored onto "stack" memory
	- Solution that needs long nested recursion will take up lots of memory space
- Recursion may not only be the only way to solve a problem
	- there may be iterative or modified recursion that does not keep too many incomplete data pending arrival of base case
- Iterative Solutions should be considered
	- iterative solutions usually involve updating over the same variable spaces so less memory is used

#### Recursion can be heavy on resources
- However there are certain problems where recursion provides a much easier to understand solution
- Recursion is fascinating to (Mathematicians) and some problems are more intuitively expressed in a recurrence relationship
- Natural candidates are like
	- Tower of Hanoi
	- Fibonacci numbers

### Fibonacci Numbers
- Denoted by F<sub>n</sub>
- forms a sequence called the Fibonacci sequence where each number is the sum of 2 preceding ones starting from 0 and 1
- F<sub>0</sub> = 0 , F<sub>1</sub> = 1
- F<sub>n</sub> = F<sub>n-1</sub> + F<sub>n-2</sub> &nbsp &nbsp    for  n>1

![[Pasted image 20250709010720.png]]

```
class TestRecursive {
	public static void main(String[] args) {
		int count = 6;
		for (int i=0; i<count; i++)
			System.out.println( “Result = ” + f(i));
		}
	}
	
	public static int f(int n) {
	 if (n == 0) return 0;         //Base Case
	 else if (n==1) return 1;      //Base Case
	 else return (f(n-1)+f(n-2));  //General Case
	}
}


```


### Tower of Hanoi

- move all the disks from x to z via y 
- only 1 disk at a time
- removed disk must be placed on one of the towers
- a larger disk cannot be placed on top of a smaller disk
![[Pasted image 20250709011258.png]]

- Base Case : first needle contains 0 disk
	- Stop recursion
- Generic Case : first needle contains only 1 or more disks
	- Recursive algorithm in pseudocode

</br>
<u>**Algorithm**</u>
- Assuming there are n disks (where n>= 1)
- Start tower x
- destination tower z
- middle tower y
- required actions:
	- Move top (n-1) disk from x to middle (using z as intermediate)
	- Move n directly from x to z
	- Move top (n-1) disk from y to z (using x as intermediate)
```
public static void move(int n, char source, char dest, char intermediate) {
	 if (n>=1) {
		 move (n-1, source, intermediate, dest);
		 System.out.println ("Move "+n+ " from "+source +" to "+ dest);
		 move (n-1, intermediate, dest, source);
	 }
}
```

![[Pasted image 20250709011905.png]]

### Big O Time Complexity
- notation represents performance of algorithm as input size grows
- notation provides upper bound (worst-case scenario) on growth rate of an algorithm's running time needed to solve a problem

- Given: an array of integers
	- int[ ] givenArray = {1,5,8,10,33,47}
- Given a method that compute the sum of all elements in a given array:
```
int getSum(int[] givenArray) {
	int[] total = 0;
		for (int i=0; i<givenArray.length; i++)
			total += givenArray[i];
	return (total);
}

```


### LinearTime Complexity

```
int getSum(int[] givenArray) {
	int[] total = 0;
	for (int i=0; i<givenArray.length; i++)
		total += givenArray[i];
	return (total);
}
```

![[Pasted image 20250709012239.png]]

![[Pasted image 20250709012249.png]]

### Drop Coefficient
```
void printItems(int[] givenArray) {
	for (int i=0; i<givenArray.length; i++)
		System.out.println(givenArray[i]);
	for (int i=0; i<givenArray.length; i++)
		System.out.println(givenArray[i]);
}

```

Number of operations = n + n = 2n

- First Rule of simplification of Big O is to drop the coefficient:
- Analysis of Time Complexity focuses on the "trend" as the input grows bigger
![[Pasted image 20250709012422.png]]

### Fastest Growing Trend
- Second rule of simplification of Big O is to take fastest growing term as it is most significant when input gets larger
![[Pasted image 20250709012506.png]]


### Quadratic Time Complexity
```
2 nested for-loops

void printItems(int n ) {
	 for (int i=0; i< n; i++)
		 for (int j=0; j< n; j++)
			 System.out.println( i + “ ” + j );
}

printItems(10):
0 0
0 1
0 2
0 3
:
:
0 9
1 0
1 1
:
:
9 7
9 8
9 9

```

![[Pasted image 20250709012714.png]]

### Constant Time Complexity
```
int squareLength (int[] a) { 
return (a.length * a.length); 
}
```

- Regardless of size of input, there is always 1 operation
 ![[Pasted image 20250709012759.png]]

### Logarithmic Time Complexity
```
void printItems(int n ) {
	for (int i=1; i< n; i=i*2)
	System.out.println( i );
}
```

![[Pasted image 20250709012829.png]]
![[Pasted image 20250709012834.png]]
![[Pasted image 20250709012845.png]]
![[Pasted image 20250709012940.png]]

### Binary Search
![[Pasted image 20250709012857.png]]
- Best case: key is found in 1st iteration
- Worst case: key is found at last round of iteration or not found
![[Pasted image 20250709012933.png]]



# Graph

- Non-linear data structure consisting of 
	- vertices
	- edges
- vertices are connected by edges
- used to represent relationships between different entities

![[Pasted image 20250801005115.png]]

- simple undirected graph has edges as bidirectional(eg, vertex 2 can go to vertex 1 and vice versa)
- simple unweighted graph has no value (such as distance) attached to its edge


- directed graph
![[Pasted image 20250801005229.png]]

- weighted graph
![[Pasted image 20250801005245.png]]

## Representation of Simple Graph
- use simple ArrayList to house all vertices 1,2,3,4,5
-  use another ArrayList for each vertex to house its neighboring vertices, aka adjacent lists (eg, edges)

![[Pasted image 20250801005359.png]]


## Traversal of Graph
- 2 fundamental methods in traversing a graph
	- Breadth First Search BFS
	- Depth First Search DFS
- aim is to visit all vertices 
- every vertex can only be visited once


### Breadth First Search
- Prepare a visited List (initially empty)
- Prepare a Queue (initially empty)
![[Pasted image 20250801005545.png]]

Steps:
1. put root vertex in queue
	a. while(queue is not empty)
		pool() a vertex from queue
		if (vertex has not been visited before)
				process vertex 
				push neighbors into queue
		repeat till queue is empty

![[Pasted image 20250801005710.png]]

![[Pasted image 20250801005725.png]]

pg 10
