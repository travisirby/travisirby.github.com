---
layout: post
title: Refactoring Fundamentals -  Notes 02
category : notes
tagline: ""
tags : [coding, best practices, csharp]
---
{% include JB/setup %}

#### Code Smell

* Context plays a large role in whether current code needs refactoring
* Named code smells provide a nomenclature to discuss code.
* Like design patterns, code smells identify area of codes that should be cleaned and why
* It is up to the developer to decide when code is too smelly.

<br />
#### Principle of Least Surprise

* *"Do what users would expect"*
*  Design API to behave as programmers would expect
*  Simple, Clear, Consistent
*  Books: Refactoring, Code Complete, Refactoring to Patterns, Clean Code

<br />
#### Eight Groups of Code Smells

1. The Bloaters
2. The Object-Orientation Abusers
3. The Change Preventers
4. The Dispensables
5. The Couplers
6. The Obfuscators
7. Environment Smells
8. Test Smells

---
#### The Bloaters
* Things that have grown out of control
* Usually happens little-by-little 

**Long Method**
* You should prefer short methods to long methods.
* There will be less duplicate code in smaller methods.
* Smaller methods lead to more descriptive names.
* Smaller methods are easier to undestand at a glance.
* How Small? 10 lines or fewer. Definitely within a screen view. 

&nbsp;

*RELATED:* 
* Long Loops (Nested Loop, Complex Logic to Break Loop)
* Functions that do more than one thing.<br />

SOLVING Long Method:
* Extract Method
	* Introduce Parameter Object
	* Replace Temp with Query
	* Replace Method with Method Object (Service)
* Compose Method
	* Replace Nested Conditional with Guard Clause
	* Replace Conditional Dispatcher with Command
	* Move Accumulation to Visitors
	* Replace Conditional Logic with Strategy

**Large Class**
* Violates Single Responsibility Principle
* Too many instance variables
* Too many private methods
	* [Iceberg Class](http://deviq.com/iceberg-class)
* Lack of cohesion
	* Some methods operate on instance variables, others with others
	* Compartmentalized Class
	* Consider Refactoring into extension methods
* *Refactoring Large Classes*
	* Extract Method (and hopefully combine logic)
	* Extract Class
	* Extract Subclass / Extract Interface
	* Replace Conditional Dispatcher with Command
	* Replace State-Altering Conditionals with State
	* Replace Implicit Language With Interpreter Pattern