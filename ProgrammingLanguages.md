# Programming Languages

## The Genealogy Of Programming Languages
![image](https://user-images.githubusercontent.com/64727012/168456695-3439ce55-a9e6-4a29-8241-1768aafe45d0.png)

## Programming Languages According To Usage
* <strong>Enterprise Programming</strong>
  * Java, Web(HTML,CSS), JavaScript, PHP, Ruby, SQL 
* <strong>Data Analysis</strong>
  * Python, R
* <strong>Embedded System Programming</strong>
  * C, C++ 
* <strong>Mobile Programmng</strong>
  * Java, Kotlin, Objective-C, Swift 
* <strong>Other Programming languages</strong>
  * Scratch - For Kids
  * Go - Google in Background
  * Scala - Improved Java, used in Spark (Big Data Platform)
  * F# - ML family on .NET (Functional PL)
  * Haskell - Modern Lisp with Concurrency
  * Groovy - Make Java as Python
  * TypeScript - Improved JavaScript, MS in Background

## Programming Paradigm
* <strong>Imperative Programming - Control Flow</strong>
  * C, BASIC 
* <strong>Functional Programming</strong>
  * Lisp, Haskell, F#
* <strong>Object-Oriented programming</strong>
  * C++, Java 
* <strong>Logic Programming</strong>
  * Prolog 
* Etc - Data Flow Programming, Event Driven Programming, Reactive Programming, Concurrent Programming

## PROs and CONs of PLs
![image](https://user-images.githubusercontent.com/64727012/168457045-2e993065-15e5-42d8-8c8e-4eaf9874ce75.png)

## Java Functional Programming
* <strong>Java8 - Functional Programming feature is added.</strong>
  * <strong>Lambda Expression</strong>
  ```java
    (int a, int b) -> a*b
  ```
  * <strong>Stream</strong>
  ```java
    long count = menu.stream()
		                  .filter(d -> d.getCalories() > 300)
		                  .distinct().limit(3).count();
  ```
## Groovy - Give Python Power to Java

### Groovy vs Java
* All Java program can run as Groovy
* Groovy can run in interpreter mode
* Groovy program is not necessary to be a Class
* Groovy program can run without main method
* Groovy is dynamic typing Language
* Groovy does not need a variable type definition – has type inference system

## Type Classification
![image](https://user-images.githubusercontent.com/64727012/168457368-7b6b91b3-f5d2-4e94-a986-35ba78e45bc2.png)
* <strong>Dynamic/Static typing</strong>
  * Dynamic typing does not need to write type because it has type inference system, but Static typing does not. 
* <strong>Strong/Weak typing</strong>
  * Strong typing is to inspect whether two data types are compatible, if they do not, to occur error or convert data type compulsorily. Conversely, Weak typing is not to inspect data type and not to be responsible for behaviors of programmers.  

## Interpreters and Compilers
![image](https://user-images.githubusercontent.com/64727012/168457685-b14da7da-b9b7-4b23-8e9a-e73a003c3177.png)

## Describing Syntax
* <strong>lexemes</strong>
  * Formal descriptions of the syntax of programming languages.
  * The lexemes of a programming language include its numeric literals, operators, and special words, among others.
  * A <strong>token</strong> of a language is a category of its lexemes.
![image](https://user-images.githubusercontent.com/64727012/168474520-daf51c8c-852f-48c5-930c-bf7a7a4631d4.png)

* <strong>Backus-Naur Form(BNF)</strong>
  * BNF is a natural notation for describing syntax.
  * <strong>A metalanguage</strong> is a language that is used to describe another language.
  * <strong>BNF</strong> is a metalanguage for programming languages.
  * BNF uses abstractions for syntactic structures.
  * e.g., 
	```
	<assign> → <id> = <expr>
	<id> → A | B | C
	<expr> → <id> + <expr>
		| <id> * <expr>
		| ( <expr> )
		| <id>
	```
  * The text on the left side of the arrow, which is aptly called the <strong>left-hand side(LHS)</strong>, is the abstraction being defined.
  * The text to the right of the arrow is the definition of the LHS. It is called the <strong>right-hand side (RHS)</strong> and consists of some mixture of tokens, lexemes, and references to other abstractions.
  * Result
  	```
	<assign> => <id> = <expr>
		=> A = <expr>
		=> A = <id> * <expr>
		=> A = B * <expr>
		=> A = B * ( <expr> )
		=> A = B * ( <id> + <expr> )
		=> A = B * ( A + <expr> )
		=> A = B * ( A + <id> )
		=> A = B * ( A + C )
	```

* <strong>Parse Tree</strong> <br/>
![image](https://user-images.githubusercontent.com/64727012/168476108-293f284b-641d-45cc-b7df-0ccc5038897c.png)

* <strong>Ambiguity</strong>
  * A = B + C * A has two distinct parse tree. The ambiguity occurs because the grammar specifies slightly less syntactic structure<br/>
![image](https://user-images.githubusercontent.com/64727012/168476256-e496121a-cd86-4c1c-8d8d-f2d019f28c39.png)

## Dynamic Semantics
1. Operational Semantics
    * The idea behind operational semantics is to describe the meaning of a statement or program by specifying the effects of running it on a machine.
2. Denotational Semantics
    * Formal method for describing the meaning of programs, Mapping function
3. Axiomatic Semantics
    * Rather than directly specifying the meaning of a program, axiomatic semantics specifies what can be proven about the program, Program Correctness Proving.

## Name, Special Words, and Variable
### Name
> A name is a string of characters used to identify some entity in a program.
### Special Words
> Special words in programming languages are used to make programs more readable by naming actions to be performed.<br/>
> A special word of a programming language that cannot be used as a name.<br/>
> It is <strong>keyword.</strong>
### Variable
* Name
* Address
* Type
* Value

## Binding
> A <strong>binding</strong> is an association between an attribute and an entity, such as between a variable and its type or value, or between an operation and a symbol.<br/>
> The time at which a binding takes place is called <strong>binding time</strong>.

### Type Bindings
> Before a variable can be referenced in a program, it must be bound to a data type. 
> The two important aspects of this binding are how the type is specified and when the binding takes place.
* <strong>Static Type Binding</strong>
  * <strong>Explicit declaration</strong> : It is a statement in a program that lists variable names and specifies that they are a particular type.
  * <strong>Implicit declaration</strong> : It is  a means of associationg variables with types through default conventions, rather than declaration statements. <strong>e.g., type inference -> var</strong>
  * Both explicit and implicit declarations create static bindings to types.
* <strong>Dynamic Type Binding</strong>
  * The variable is bound to a type when it is assigned a value in an assignment statement.
  * It is important to realize that the type of a variable whose type is dynamically bound may be temporary.
  * The primary advantage of dynamic binding of variables to types is that it provides more programming flexibility. 
  * For example, a program to process numeric data in a language that uses dynamic type binding can be written as a generic program, meaning that it is capable of dealing with data of any numeric type.
### Storage Bindings and Lifetime
> The memory cell to which a variable is bound somehow must be taken from a pool of available memory. 
> This process is called <strong>allocation. <br/>Deallocation</strong> is the process of placing a memory cell that has been unbound from a variable back into the pool of available memory.<br/>
> The <strong>lifetime</strong> of a variable is the time during which the variable is bound to a specific memory location.
* <strong>Static Variables</strong>
  * <strong>Static variables</strong> are those that are bound to memory cells before program execution begins and remain bound to those same memory cells until program execution terminates.
* <strong>Stack-Dynamic Variable</strong>
  * <strong>Stack-dynamic variables</strong> are those whose storage bindings are created when their declaration statements are elaborated, but whose types are statically bound.
  * <strong>Elaboration</strong> of such a declaration refers to the storage allocation and binding process indicated by the declaration, which takes place when execution reaches the code to which the declaration is attached. Therefore, elaboration occurs during run time.
* <strong>Explicit Heap-Dynamic Variable</strong>
  * <strong>Explicit heap-dynamic variables</strong> are nameless (abstract) memory cells that are allocated and deallocated by explicit run-time instructions written by the programmer.
  * These variables, which are allocated from and deallocated to the heap, can only be referenced through pointer or reference variables.
* <strong>Implicit Heap-Dynamic Variable</strong>
  * <strong>Implicit Heap-Dynamic Variable</strong> bound to heap storage only when they are assigned values. In fact, all their attributes are bound every time they are assigned, JavaScript

## Scope

### Static Scope
* Scope of a variable can be statically determined.
* Nested static scopes : Ada, JavaScript, Common LISP, Scheme, Fortran 2003+, F#, Python, JavaScript Example
* Not nested static scopes : C, Java

### Dynamic Scope
* APL, SNOBOL4, and the early versions of LISP
* Dynamic scoping is based on the calling sequence of subprograms

## Data Types

### Primitive Types
* byte, short, int, long, float, double, char, boolean
* one byte - true false / 0, null - false, otherwise - true

### String Types
* In Java, String is object class and immutable, but StringBuffer and StringBuilder is mutable.

### Enumeration Types
* Java enum
```java

enum MyFavoriteColor {RED, BLUE, GREEN, YELLOW};
MyFavoriteColor color = MyFavoriteColor.BLUE;


```
* C++ enum
```cpp

enum class Color { red, blue, green };
Color col = Color::red;

```


### Array Types
* Array is a homogeneous aggregate of data elements in which an individual element is identified by its position in the aggregate.
* All elements are same type.
* Elements of generic arrays are references to objects.
* In Java, Array is a kind of class type.
* Jagged Arrays( Ragged Arrays) - one in which the lengths of the rows need not be the same.<br/>
![image](https://user-images.githubusercontent.com/64727012/169301890-6daedec4-4040-4d5b-aea8-bb5e5882630b.png)

### Record Types
* Record is an aggregate of data elements in which the individual elements are identified by names and accessed through offsets from the beginning of the structure.
```cpp
struct { 
	int id;
	double num;
}

```

### Tuple Types
* Tuple is similar to a record, except that the elements are not named.
* Python, immutable tuple
```python
myTuple = (3, 5.8, 'apple’)
myTuple[1]  – first element
# Tuple index starts from 1.

```

### List Types
* Lisp
* ML
  * all elements are same type
  ```ml
  [5, 7, 9]
  
  ```
* Python
  * elements are any data value or object
  ```python
  myList = [3, 5.8, "grape"]
  x = myList[1]  	# x is 5.8
  r = range(1, 6) # r is [1, 2, 3, 4, 5]
  ```

### Union, Pointer, Reference (C, C++)
* Union
  * Variables of Union can store different type values at different times in same location.
  ```cpp
  union { 
	  int id;
	  double num;
  }
  ```
* Pointer
  * Variables of Pointer have a range of values of memory addresses.
  ```cpp
  int* px;
  ```
* Reference
  * Reference refers  to an object or a value in memory
  ```cpp
  int result = 0;
  int &ref_result = result;
  ref_result = 100; // result is 100
  ```

### Class Types, Fuction Types
* Class Type (Object-Oriented Programming)
  * In Java all non-primitive types are Class type.
  * Variable Name represents reference of a class instance.
  * In python and groovy, All numeric types are class type.
* Function Types (Functional Programming)
  * Functions as first-class citizens
    1. passing functions as arguments to other functions
    2. returning functions as the values from other functions
    3. assigning functions to variables
 
### Type Checking
* Checking the operands of an operator are of compatible types.
* Compatible type – legal for the operator or allowed under implicit language rules(coercion)
* Coercion – Automatic conversion
* Type error – In case of the application of an operator to an operand of an inappropriate type
* According to Type Checking time, classifying Dynamic type checking, Static type checking
* According to rigidity of Type Casting, classifying Strong Typing, Weak Typing

#### Classifying Type Checking
![image](https://user-images.githubusercontent.com/64727012/168457368-7b6b91b3-f5d2-4e94-a986-35ba78e45bc2.png)
 
#### Static Type vs Dynamic Type
* Static Type Checking – all bindings of variables to types are static<br/>
e.g., Ada, C, C++ C#, COBOL, F#, Fortran, Go, Haskell, Java, Kotlin, ML, Modula-2, Pascal, Rust, Scala, Swift

* Dynamic type checking – type checking at run time<br/>
e.g., Clojure, Erlang, Groovy, JavaScript, Lisp, Lua, Objective-C, Perl, PHP, Prolog, Python, R, Ruby, Scratch

#### Strong Type vs Weak Type
* strongly typed – type safe(prevent type error), type safe coercion<br/>
e.g., Java, Python, Groovy, C#, Ruby


* weakly typed – void* of C, unsafe operation, indiscreet coercion, Union type<br/>
e.g., C, C++, JavaScript, Perl

### Type Equivalence
* Type compatibility – the types of operands that are acceptable for each of the operators 
* Type Equivalence – an operand of one type in an expression is substituted for one of the other type, without coercion. compatibility without coercion
* Name type equivalence – the same declaration or in declarations that use the same type name
* Structure type equivalence – identical structures(same tree structure)

## Operator Evaluation Order
* Precedence <br/>
![image](https://user-images.githubusercontent.com/64727012/169315715-9299fbd7-e37a-4d2a-8b59-6e80400b69c4.png)

* Associativity<br/>
![image](https://user-images.githubusercontent.com/64727012/169315723-cf2737bf-d928-46d0-98ea-10594f7ea3ee.png)

* Java Operator Precedence
![image](https://user-images.githubusercontent.com/64727012/169315886-646ce76e-95e7-407b-8b8e-1cdfc0e8fd1a.png)

## Side Effects
> Function chages either one of its parameters or a global variable.

## Operator overloading
> Multiple use of an operator, e.g., can use + as int +, float + or String +. We can define functions related to operator according to PL.

## Type Conversions
* Coercion
  * Type conversion occurs implicitly as conventions for implicit operand type conversions
    * C++, Java, C# -- widening
    * ML and F# do not coerce operands in expressions
* Type Cast
  * explicit type conversions 
    * Java
    ```java
    (int)angle
    ```
    * C++
    ```cpp
    static_cast<int>(angle)
    ```
## Short-Circuit Evaluation
> Result is determined without evaluationg all of the operands and.or operators.<br/>
> ``` if((a>=0)&&(b<10)) ``` if a<0, no more evaluation.

## Control Structures
> Selection statements, e.g., if/else

## Multiple-Selection statements
> e.g., switch

## Implementing Multple Selection structures
* Python
```python

if count < 10 :
    bag1 = True
elif count < 100 :
    bag2 = True
elif count < 1000 :
    bag3 = True

```
* Java
```java

if (count < 0)
    bag1 = true;
else if (count < 100)
    bag2 = true;
else if (count < 1000)
    bag3 = true;

```

## Iterative Statements (Loop)
> e.g., for

## Logically Controlled Loops
> e.g., while, do-while

<strong>Reference</strong>
* Robert W. Sebestra, "Concepts Of Programming Languages, 10th Edition"

