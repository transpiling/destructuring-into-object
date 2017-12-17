# Destructuring into object (EcmaScript proposal)

If you prefer to initiate your classes via property list (props), you should like ES7 destructuring assigment syntax:

	class Abc {
	    constructor(props = {a:1, c:3}){
	        ({
	            a: this.a,
	            b: this.b = 2,
	            c: this.c,
	        } = props)
	    }
	}
	
	console.log(new Abc) // Abc {a:1, b:2, c:3} 
	
(try in your Browser console | [compatibility])

Cool, but that syntax can be more sweet. So, I propose new EcmaScript construction for this case:

	
	class Abc {
	    constructor(props = {a:1, c:3}){
	        this.{
	            a,
	            b = 2,
	            c,
	        } = props
	    }
	}
	

Please star, if you like) And I will create babel plugin.  

[Read more](http://exploringjs.com/es6/ch_destructuring.html#sec_assignment-targets)

[compatibility]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#Browser_compatibility

