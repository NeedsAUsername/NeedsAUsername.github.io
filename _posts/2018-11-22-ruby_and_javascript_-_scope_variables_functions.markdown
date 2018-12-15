---
layout: post
title:      "Ruby and Javascript - Scope, Variables, Functions"
date:       2018-11-22 19:52:41 -0500
permalink:  ruby_and_javascript_-_scope_variables_functions
---


<p>There's quite a few differences in how scope, variables, and functions are treated in Ruby versus in Javascript. 

To start off, Javascript uses lexical scoping, meaning that inner functions/closures have access to outer functions further up its scope chain. 
</p>

```
function outer() 
  let outerVar = 'hello'; 
	function innerVar() {
	  console.log(outerVar);
	}
	innerVar();
}

outer() // hello
```

<p>
Ruby methods, on the other hand, are closed off from all information outside of it. Inside Ruby methods, the only variables in scope are the ones declared within the function, and those passed through in arguments.  
</p> 

```
outerVariable = 'hello' 

def any_method 
  puts outerVariable
end 

any_method // undefined local variable or method `outerVariable' 
```
<p>
In Ruby, methods aren't treated like functions in other languages; they can't be passed to other methods as arguments, returned by other methods, or assigned to a variable (thus, there is no way to reference a Ruby method). In order words, Ruby methods can only return values, and Ruby variables can only hold values. (If you do need some of these features, look into Ruby Procs)
```

<p>In Javascript, however, functions are treated as first-class citizens, which is just a fancy way of saying that they are treated just like other plain variable. This enables functions to be declared and passed as arguments (We're going to be using an immediately invoked function so its value is passed instead of the function itself). 
</p>

```
function sayWord(word) {
  console.log(word)
} 

sayWord( word = 'hello') // hello

sayWord( (function(){return 'hello'})() ) // hello

``` 

<p>
Javascript's arguments are also optional, whereas Ruby's arguments are required and will bring up an error if you don't provide them. As we can see, these languages take different approaches to writing code, each with their own style and personality. 
</p>
<p>When it comes to functions and variable scoping, Javascript is flexible; it can create functions within arguments, and it allows all functions to access all variables above it in its scope chain. This freedom may come at a price, however, as variables can change and shift unexpectedly, as functions can easily change their values. 
</p> 
<p> 
On the other hand, Ruby is strict. Many people analogize Ruby methods to a living cell; self-reliant and only filtering in explicitly necessary outside resources through its cell walls. Planned, and methodical, this approach may seem limiting, but is less prone to variable mishaps, as every method is self-contained, and you're never unsure about a variable's value (unless you directly change a variable's value, it will always hold the same value that you declared it with). 
</p>






