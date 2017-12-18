[![](http://truejs.com/content/images/2016/07/destructuring-1.png)](http://exploringjs.com/es6/ch_destructuring.html)

# Destructuring into object

If you assign via destructuring, each assignment target can be everything that is allowed on the left-hand side of a normal assignment.
```js
let src = {a:1,b:2,c:3}, target = {};     
	
({a: target.a} = src);  
	
console.log(target); // {a:1}
```

But that syntax isn't very userful, especially for assigning to many properties:
```js	
({a: target.a, b:target.b, c:target.c} = src)
```

### Read more
[You can assign to more than just variables](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

# ECMAScript 2018 proposal

So, I want to propose this sugar:
```js	
target.{a,b,c} = src
```
+ This syntax is more clear and understandable: even without ES2015 knowleges, any experienced developer can assume that some properties assigned to the left-side `target` from right-side `src` variable.
+ You can omit braces `()` becouse statement doesn't starts with `{` now.  

# Babel plugin

Please star, to start) And I will create babel plugin. 

