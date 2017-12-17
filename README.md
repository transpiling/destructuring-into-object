# Destructuring into object (EcmaScript proposal)

If you assign via destructuring, each assignment target can be everything that is allowed on the left-hand side of a normal assignment.
```js
let src = {a:1,b:2,c:3}, target = {};     
	
({a: target.a} = src);  
	
console.log(target); // {a:1}
```

But that syntax isn't very good, especially for assigning to many properties:
```js	
({a: target.a, b:target.b, c:target.c} = src)
```
So, I propose this sugar:
```js	
target.{a,b,c} = src
```
+ This syntax is more clear and understandable: even without ES6 knowleges, developer can assume that some properties assigned to left-side `target` from right-side `src` variable.
+ You can omit braces `()` becouse statement doesn't starts with `{` now.  


Please star, if you like) And I will create babel plugin.  

[Read more about destructuring...](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

