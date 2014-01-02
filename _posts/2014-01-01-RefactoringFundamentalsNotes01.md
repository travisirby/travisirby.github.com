---
layout: post
title: Refactoring Fundamentals -  Notes 01
category : notes
tagline: ""
tags : [coding, best practices, csharp]
---
{% include JB/setup %}

#### Why Should You Refactor?

* Improves Design and Readability
* Will uncover mistakes and reveal defects.
* Rereading code is important.
* It keeps technical debt low.


#### Technical Debt

* Originally coined by Ward Cunningham in the '90s:
> Shipping first time code is like going into debt. A little
>debt speeds development so long as it is paid back promptly
>with a rewrite \[refactoring\]… The danger occurs when the debt
>is not repaid. Every minute spent on not-quite-right code
>counts as interest on that debt. Entire engineering organizations 
>can be brought to a standstill under the debt load of an
>unconsolidated implementation. -Ward

#### When Should You Refactor?

* Shutting down progress completely to refactor should be avoided
	* This will lead to the same negative pattern in the future.
* If a part of the system is causing you pain.
* When it will make implementing a new function easier.
* TDD Red-Green-Refactor
* As part of the process of fixing bugs.
* As part of code reviews. Pair programing.

#### When Should You Not Refactor?

* Massive Technical Debt:
	* Declare Technical Bankruptcy, Rewrite
* Current Code is not working
	* This can lead down a rabbit hole.
	* TDD insists only refactor while all tests green.
* Imminent Deadline
	* Accept the technical debt, Repay later
	
>  Other than when you are very close to a deadline, however, you 
should not put off refactoring because you haven't got time. Experience
with several projects has shown that a bout of refactoring results 
in increased productivity. Not having enough time usually is a sign
that you need to do some refactoring. - Martin Fowler
 

#### Refactoring Principles

* Keep it simple
* Keep it DRY (Don't Repeat Yourself)
* Make it Expressive
	* Strive for self-documenting code
*  Reduce Overall Code
	* Unless it would make it less expressive or more complex
	* Avoid cryptic, terse code.

#### Kent Beck's Rules of Simple Design
##### (in priority order)

1. Run all the tests (successfully)
2. Contain no duplicate code
3. Express all the ideas the author wants to express
4. Minimize classes and methods


#### *Boy Scout Rule of Coding*
#### *Leave Your Code Better Than You Found It*

