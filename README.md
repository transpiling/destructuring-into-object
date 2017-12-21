[![](http://truejs.com/content/images/2016/07/destructuring-1.png)](http://exploringjs.com/es6/ch_destructuring.html)

Destructuring into object
-------------------------

[(You can assign to more than just variables)](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

If you assign via destructuring, each assignment target can be everything that is allowed on the left side of a normal assignment.

	let srcObject = {a:1,b:2,c:3}, target = {};     
	
	({a: target.a} = srcObject);  
	
	console.log(target); // {a:1}
	
## Problem

ES6 destructuring syntax isn't very useful, especially for assigning to properties of other object:
```js
	// ES6
	({
	    a: target.a,
	    b: target.b,
	    c: target.c,
	} = srcObject);
	
	// Versus ES3
	target.a = srcObject.a;
	target.b = srcObject.b;
	target.c = srcObject.c;
```
- identifiers are still duplicated (there is no reason to start using new ES6 syntax, old syntax is better)
- there is hard to assume that `target` object will be modified, if developer do not know ES6
- you should write braces `()` or use other solution, because JS statement cannot starts with `{`

## Proposal

So, in addition to current syntax, I want to propose this sugar:

	target.{a,b,c} = srcObject

#### Why?

+ This syntax is more clear and understandable:    
  even without ES6/ES2015 knowleges, experienced developer can assume that some properties assigned to the left-side `target` from a right-side `srcObject` variable.
+ The destructuring goal is met: full elimination of identifiers duplication.
+ You can omit braces `()` because JS statement doesn't starts with `{` now.  
	
#### Extract object properties into local variables

	let * = {a:1, b:2} // like import * from 'module'
	console.log(a, b) // 1 2

#### New syntax for Object.assign()

	let target = {a:0}
	
	target.* = {b:1, c:2}
	// or target.{} = ...
	
	console.log(target) // {a:0, b:1, c:2}
	
Useful for:

+ adding props to the `this` object in class constructor
+ adding methods to the prototype of class, when building custom classes

## Babel plugin

Please star, to start) And I will create babel plugin. 

