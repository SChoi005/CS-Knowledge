# Object-Oriented Programming

## Class Name
> By convention, class names start with an uppercase letter. <br/>
> Capitalize the first letter of each word in the name. ex) ComputeExpression

## Named Constants
> Capitalize all letters in constants, and use underscores to connect words.

```java
  final datatype CONSTANT_NAME = VALUE;
```

## Variables and method names
> Use lowercase for the first word.<br/>
> Capitalize the first letter of each subsequent word in the name.

## Software Development Process
![image](https://user-images.githubusercontent.com/64727012/168081566-e65b4370-0a30-4fa9-b28f-2a549c8e0e03.png)

### 1. Requirement Specification
> A process that seeks to understand the problem and document in detail what the software system needs to do.
> This phase involves close interaction between users and designers.

### 2. System Analysis
> Seeks to analyze the business process in terms of data flow, and to identify the system's input and output.
> Part of the analysis entails modeling the system's behavior. 
> The model is intended to capture the essential elements of the system and to define services to the system.

### 3. System Design
> The process of designing the system's component
> This phase involves the use of many levels of abstraction to decompose the problem into manageable components, identify classes and interfaces, and establish relationships among the classes and interfaces.

#### IPO
> The essence of system analysis and design is input, process, and output. This is called IPO.

### 4. Implementation
> The process of translating the system design into programs.
> Seperate programs are written for each component and put to work together.
> The implementation involves coding, testing, and debugging.

### 5. Testing
> Ensures that the code meets the requirements specification and weeds out bugs.

### 6. Deployment
> Deployment makes the project available for use. For a java program, this means installing it on a desktop or on the Web.

### 7. Maintenance
> This requires periodic upgrades of the product to fix newly discovered bugs and incorporate changes.

## Operator Associativity
> All binary operators except assignment operators are left-associative. ex) a-b+c-d => ((a-b)+c)-d
> Assignment operators are right-associative. ex) a=b+=c=5 => a=(b+=(c=5))

## Mathematical Functions
> Java provides many useful methods in the <strong>Math</strong> class for performing common mathematical functions.

## Unicode Format
> Java characters use <strong>Unicode</strong>, and display of written texts in the world;s divers languages.
> Unicode takes two bytes, preceded by \u, expressed in four hexadecimal numbers that run from '\u0000' to '\uFFFF'.

## Character Class
> There are methods like isDigit, isLetter, toLowerCase, etc.

## String type
> Stirng is actually a predefined class in the Java library. The String type is not a primitive type. It is know as a reference type. <br/>
> In String class, there are many useful and confortable methods.

## Arrays
> The arrays are stored in a heap. In Array class, there are many useful and confortable methods.

## Object-oriented programming Concepts
> OOP involves programming using objects.
> An object represents an entity in the real world that can be distinctly identified. ex) a student, a desk, a circle, etc.
> An object has a unique identity, statem and behaviors.
> The state of an object consists of a set of data fields.
> The behavior of an object is defined by a set of methods.

## Classes
### A Java class uses
<ul>
  <li>variables to define data field</li>
  <li>methods to define behaviors</li>
  <li>constructors</li>
</ul>

## Garbage Collection
> After the assignment statement c1 = c2, c1 points to the same object referenced by c1 is no longer referenced.
> This object is known as garbage. Garbage is automatically collected by JVM.

## Static Variables, Constants, and Methods
> Static variables are shared by all the instances of the class.
> Static methods are not tied to a specific object.
> Static constants are final variables shared by all the instances of the class.

## Why Data Fields Should Be private?
<ul>
  <li>To protect data</li>
  <li>To make code easy to maintain</li>
</ul>

## Immutable Objects and Classes
> If the contents of an object cannot be changed once the object is created, the object is called an <strong>immutable object</strong> and its class is called an <strong>immutable class</strong>.

### What Class is Immutable?
* For a class to be immutable, it must mark all data fields private and provide no mutator methods and no accessor methods that would return a reference to a mutable data field object.

## Class Abstraction and Encapsulation
* Class abstarction means to separate class implementation from the use of the class.
* The creator of the class provides a description of the class and let the user know how the class can be used.
* The user of the class does not need to know how the class is implemented. The detail of implementaion is encapsulated and hidden from the user.

## Designing a Class
* A class should describe a single entity, and all the class operations should logically fit together to support a coherent purpose. For example, you should not combine students and staff in the same class, because students and staff have different entities. 
* A single entity with too many responsibilities can be broken into several classes to separate responsibilities.
* For example, the classes <strong>String</strong>, <strong>StringBuilder</strong>, and <strong>StringBuffer</strong> all deal with strings, but have different responsibilities.
* Classes are designed for reuse.
* Follow standard Java programming style and naming conventions.
* Choose informative names for classes, data fields, and methods.
* Always place the data declaration before the constructor, and place constructors before methods.
* Always provide a constructor and initialize variables to avoid programming errors.

## Using Visibility Modifiers
* A class should use the private modifier to hide its data from direct access by clients.
* You can use get methods and set methods to provide users with access to the private data, but only to private data you want the user to see or to modify.
* A class should also hide methods not intended for client use.
* Make the fields or method protected if they are intended for extenders of the class.

### Using the static Modifier
* A property that is shared by all the instances of the class should be declared as a static property.

## Object Composition
* Composition is actually a special case of the aggregation relationship.
* Aggregation models has-a relationships and represents an ownership relationship between two objects.
* The owner object is called an aggregating object and its class an aggregating class. 
* The subject object is called an aggregated object and its class an aggregated class.
![image](https://user-images.githubusercontent.com/64727012/168294169-5a0ae1be-f0bf-4f0e-bb11-459759d411d0.png)

## Userful Java Class Utils
### Wrapper Classes
> Boolean, Character, Short, Byte, Integer, Long, Float, Double
* The wrapper classes do not have no-arg constructors
* The instances of all wrapper classes are immutable. i.e., their internal values cannot be changed once the objects are created.
### String class
* A String object is immutable. i.e., its contents cannot be changed. 
#### Interned Strings
> Since strings are immutable and are frequently used, to improve efficiency and save memory, the JVM uses a unique instance for string literals with the same character sequence. Such an instance is called interned. For example, the following statements:
![image](https://user-images.githubusercontent.com/64727012/168296256-ff20c225-eeac-426b-af10-d0498309f032.png)

## String Builder and StringBuffer
> The calsses is an alternative to the String class. In general, a StirngBulder/StringBuffer can be used wherever a string is used.StringBuilder/StringBuffer is more flexible than String. You can add, insert, or append new contents into a string buffer, whereas the value of a String object is fixed once the string is created.

## Are superclass's Constructor Inherited?
> They are not inherited. They are invoked explicitly or implicitly. <br/>
> Explicitly using the <strong>super</strong> keyword.<br/>
> If the keyword <strong>super</strong> is not explicitly used, the  superclass's no-arg constructor is automatically invoked. the compiler puts <strong>super()</strong> as the first statement in the constructor.

### Using the Keyword super
* To call a superclass constructor
* To call a superclass method

## Defining a Subclass
### You can also :
* Add new properties
* Add new methods
* Override the methods of the superclass
### NOTE
* An instance method can be overridden only if it is accessible
* Thus a private method cannot be overridden, because it is not accessible outside its own class.
* If a method defined in a subclass is private in its superclass, the two methods are completely unrelated.
* Like an instance method, a static method can be inherited.
* However, a static method cannot be overridden.
* If a static method defined in the superclass is redefined in subclass, the method defined in the superclass is hidden.

## The Object class and Its Methods
> Every class in Java is descended from the java.lang.Object class. If no inheritance is specified when a class is defined, the superclass of the class is Object.
* toString() method

## Polymorphism
> Polymorphism means that a variable of a supertype can refer to a subtype object.<br/>
> An object of a subtype can be used wherever its supertpe value is required.
![image](https://user-images.githubusercontent.com/64727012/168409589-a7f0b1da-2bce-42ad-bd86-8b1b02cabe79.png)

## Dynamic Binding
1. Suppose an object o is an instance of classes : C1,C2,...,Cn-1 and Cn.<br/>
2. C1 is most specific class, Cn is most general class. In java, Cn is the Object class. <br/>
3. If o invokeds a method p, the JVM in turn searches the implementation for the method p in C1,C2,...,Cn-1, and Cn, until it is found.<br/>
4. Once an implementation is found, the search stops and the first-found implementation is invoked.

## Casting Object
> You have already used the casting operator to convert variables of one primitive type to another. Casting can also be used to convert an object of one class type to another within an inheritance hierarchy.

### Why Casting Is Necessary?
* Why does the statement <strong>Object o = new Student()</strong> work and the statement <strong>Student b = o</strong> doesn’t?
* This is because a Student object is always an instance of Object, but an Object is not necessarily an instance of Student.
* Even though you can see that o is really a Student object, the compiler is not so clever to know it.
* To tell the compiler that o is a Student object, <strong>use an explicit casting</strong>.
* Ex)<strong> Student b= (Student)o; </strong>
* Explicit casting must be used when casting an object from a superclass to a subclass.

## The instatnceof Operator
Use the instanceof operator to test whether an object is an instance of a class.

## Accessibility Summary
![image](https://user-images.githubusercontent.com/64727012/168410354-d76265c8-7b2f-4363-be2b-381e858e7bc2.png)
### A Subclass Cannot Weaken the Accessibility
* A subclass may override a protected method in its superclass and change its visibility to public.
* However, a subclass cannot weaken the accessibility of a method defined in the superclass.
For example, if a method is defined as public in the superclass, it must be defined as public in the subclass.

## The final Modifier
* The final class cannot be extended
* The final variable is a constant
* the final method cannot be overridden by its subclasses.

## The ArrayList Class
>You can create an array to store objects. But the array’s size is fixed once the array is created. Java provides the ArrayList class that can be used to store an unlimited number of objects.

### Generic Type
> ArrayList is known as a generic class with a generic type E.<br/>
> You can specify a concrete type to replace E when creating an ArrayList. <br/>
> For example, the following statement creates an ArrayList and assigns its reference to variable cities. <br/>
> This ArrayList object can be used to store strings.
```java

ArrayList<String> cities = new ArrayList<String>();
ArrayList<String> cities = new ArrayList<>();

```

## Exception Handling

### Exception Types
![image](https://user-images.githubusercontent.com/64727012/168411048-c1a60148-ea25-4c20-815e-e661709b2a2a.png)

#### System Errors
> System errors are thrown by JVM and represented in the <strong>Error</strong> class.
> The <strong>Error</strong> class describes internal system error. 
> Such errors rarely occur. 
> If one does, there is little you can do beyond notifying the user and trying to terminate the program gracefully.

#### Exceptions
> <strong>Exception</strong> describes errors caused by your program and external circumstances. 
> These errors can be caught and handled by your program.

* Runtime Exceptions
  * RuntimeException is caused by programming errors, such as bad casting, accessing an out-of-bounds array, and numeric errors.

#### Checked Exceptions vs Unchecked Exceptions
> <strong>RuntimeException, Error</strong> and their subclasses are known as <strong>unchecked exceptions.</strong> <br/>
> All other exceptions are known as <strong>checked exceptions</strong>, meaning that the compiler forces the programmer to check and deal with the exceptions.
* Unchecked Exceptions
  * In most cases, unchecked exceptions reflect programming logic errors that are not recoverable. These are the logic errors that should be corrected in the program.

### Cautions When Using Exceptions
> Exception handling separates error-handling code from normal programming tasks, thus making programs easier to read and to modify.

### When to Throw Exceptions
> An exception occurs in a method. If you want the exception to be processed by its caller, you should create an exception object and throw it. If you can handle the exception in the method where it occurs, there is no need to throw it. <br/>
> You should use it to deal with unexpected error conditions. <br/>
> Do not use it to deal with simple, expected situations.

  ```java
  try {
    System.out.println(refVar.toString());
  }
  catch (NullPointerException ex) {
    System.out.println("refVar is null");
  }
  
  /* is better to be replaced by */
  if (refVar != null)
    System.out.println(refVar.toString());
  else
    System.out.println("refVar is null");
  ```
### Defining Custom Exception Classes
* Use the exception classes in the API whenever possible.
* Define custom exception classes if the predefined classes are not sufficient.
* Define custom exception classes by extending Exception or a subclass of Exception.

### Assertions
> An assertion is a Java statement that enables you to assert an assumption about your program. 
> An assertion contains a Boolean expression that should be true during program execution. 
> Assertions can be used to assure program correctness and avoid logic errors.

### Using Exception Handling or Assertions
* Assertion should not be used to replace exception handling. Exception handling deals with unusual circumstances during program execution. Assertions are to assure the correctness of the program.
* Do not use assertions for argument checking in public methods. Valid arguments that may be passed to a public method are considered to be part of the method’s contract.
* Use assertions to reaffirm assumptions. This gives you more confidence to assure correctness of the program.

## The File Class
> The File class is a wrapper class for the file name and its directory path.
![image](https://user-images.githubusercontent.com/64727012/168412343-60f4029c-0df1-4c39-ab25-4b5864bd5345.png)

## Text I/O
> In order to perform I/O, you need to create objects using appropriate Java I/O classes.
* Scanner class for writing data
![image](https://user-images.githubusercontent.com/64727012/168412446-563511f2-37bf-4ff3-8ab3-41807347c4b2.png)

* PrintWriter class for reading data
![image](https://user-images.githubusercontent.com/64727012/168412434-39a221b9-9410-4704-9a5f-53c040dd627a.png)

### Reading Data from the Web
> Just like you can read data from a file on your computer, you can read data from a file on the Web.

```java

URL url = new URL("www.google.com/index.html");
Scanner input = new Scanner(url.openStream());

```


<strong>Reference</strong>
* Y. Daniel Liang, "Introduction to Java Programming, 10th Edition"
