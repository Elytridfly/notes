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
	- 