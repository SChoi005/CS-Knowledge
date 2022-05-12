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

Chapter 10
