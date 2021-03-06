- [ES-discuss mailing list](https://mail.mozilla.org/pipermail/es-discuss/2018-February/050279.html) (Preparation for the [TC39 Process](https://tc39.github.io/process-document/))

[![](http://truejs.com/content/images/2016/07/destructuring-1.png)](http://exploringjs.com/es6/ch_destructuring.html)

Subject: Destructuring into object
----------------------------------
>
> If you assign via destructuring, each assignment target can be everything that is allowed on the left side of a normal assignment.
> ```js
>	let srcObject = {a:1,b:2,c:3}, target = {};     
>	
>	({a: target.a} = srcObject);  
>	
>	console.log(target); // {a:1}
> ```
> _[(You can assign to more than just variables)](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)_

## The Problem

ES6 destructuring syntax isn't very readable and useful, in case with assigning to properties of existing object:
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
There is no reasons to start using new ES6 destructuring syntax now, old syntax is better, because:
- there is hard to assume that `target` object will be modified, if developer does not familar with new standart
- identifiers are still duplicated
- you should write braces `()` or use other solution, because JS statement cannot starts with `{`

## Proposal

So, in addition to current ES6 syntax, I want to propose this sugar:
```js
	target.{a,b,c} = srcObject
	//alternative// target.* = srcObject{a,b,c}
```
#### Why?
+ This syntax is more clear and understandable:    
  even without ES6 knowleges, developer can assume that some properties assigned to the left-side `target` from a right-side `srcObject` variable.
+ The one of destructuring goal is met: full elimination of identifiers duplication.
+ You can omit braces `()` because JS statement doesn't starts with `{` now.  

#### New syntax for Object.assign()
```js
	let target = {a:0}
	
	target.* = {b:1, c:2}
	//alternative// target.{} = ...
	
	console.log(target) // {a:0, b:1, c:2}	
```
Useful for:

+ adding properties to the `this` object in constructor
+ adding methods to the prototype of class
	
#### Extracting properties into local variables
```js
	let * = {a:1, b:2} // like import * from 'module'
	console.log(a, b) // 1 2
```

## Babel plugin
Please star, to start) And I will create babel plugin. 

