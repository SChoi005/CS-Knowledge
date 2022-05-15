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







<strong>Reference</strong>
* Robert W. Sebestra, "Concepts Of Programming Languages, 10th Edition"

