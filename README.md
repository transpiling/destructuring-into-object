[![](http://truejs.com/content/images/2016/07/destructuring-1.png)](http://exploringjs.com/es6/ch_destructuring.html)

Destructuring into object
-------------------------

[(You can assign to more than just variables)](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

If you assign via destructuring, each assignment target can be everything that is allowed on the left side of a normal assignment.

	let srcObject = {a:1,b:2,c:3}, target = {};     
	
	({a: target.a} = srcObject);  
	
	console.log(target); // {a:1}
	
## Problem

Current syntax isn't very useful, especially for assigning to many properties:

	({a: target.a, b:target.b, c:target.c} = srcObject)

## Proposal

So, in addition to current syntax, I want to propose this sugar:

	target.{a,b,c} = srcObject

#### Why?

+ This syntax is more clear and understandable:    
  even without ES6/ES2015 knowleges, experienced developer can assume that some properties assigned to the left-side `target` from a right-side `srcObject` variable.
+ The destructuring goal is met: elimination of identifiers duplication.
+ You can omit braces `()` because statement doesn't starts with `{` now.  
	
#### Explode object into local variables

	let * = {var1:1, var2:2} // like import * from 'some-module'
	console.log(var1, var2) // 1 2

#### Object.assign() new syntax

	let target = {var0:0}
	
	target.* = {var1:1, var2:2}
	// or target.{} = ...

	console.log(target) // {var0:0, var1:1, var2:2}

## Babel plugin

Please star, to start) And I will create babel plugin. 

