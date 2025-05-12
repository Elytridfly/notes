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