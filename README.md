# Destructuring into object (EcmaScript proposal)

If you assign via destructuring, each assignment target can be everything that is allowed on the left-hand side of a normal assignment.

	let in = {b:2,c:3,d:4}, out = {a:1}     
	
	({b: out.b} = in)  
	
	console.log(out) // {a:1,b:2}
	

But that syntax isn't very good, especially for assigning to many properties:
	
	({b:out.b, c:out.c, d:out.d} = in)

So, I propose this sugar:
		
	out.{b,c,d} = in
	
+ This syntax is more clear and understandable: even without ES6 knowleges, developer can assume that some properties assigned to left-side `out` from right-side `in` variable.
+ You can omit braces `()` becouse statement doesn't starts with `{` now.  


Please star, if you like) And I will create babel plugin.  

[Read more about destructuring](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

