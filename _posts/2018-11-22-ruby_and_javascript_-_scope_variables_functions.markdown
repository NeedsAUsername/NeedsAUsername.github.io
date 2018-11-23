---
layout: post
title:      "Ruby and Javascript - Scope, Variables, Functions"
date:       2018-11-22 19:52:41 -0500
permalink:  ruby_and_javascript_-_scope_variables_functions
---


<p>There's quite a few differences in how scope, variables, and functions are treated in Ruby versus in Javascript. 

To start off, Javascript uses lexical scoping, meaning that inner functions/closures have access to outter functions further up its scope chain. 
</p>

```
function outter() 
  let outterVar = 'hello'; 
	function innerVar() {
	  console.log(outterVar);
	}
	innerVar();
}

outter() // hello
```

<p>
Ruby methods, on the other hand, are closed off from all information outside of it. Inside Ruby methods, the only variables in scope are the ones declared within the function, and those passed through in arguments.  
</p> 

```
outterVariable = 'hello' 

def any_method 
  puts outterVariable
end 

any_method // undefined local variable or method `outterVariable' 
```

In Ruby, variables can be created in arguments, but methods can not. Not to mention it just looks really awkward with Ruby's def/end syntax.
```
def say_word(word)  
  puts word 
end 

say_word(word =  'hello') // hello 

say_word(def word 'hello' end) // syntax error
```

In Javascript, however, functions are treated as first-class citizens, which is just a fancy way of saying that they are treated just like other plain variable. This enables functions to be declared and passed as arguments (We're going to be using an immediately invoked function so its value is passed). 

```
function sayWord(word) {
  console.log(word)
} 

sayWord('hello') // hello

sayWord( (function(){return 'hello'})() ) // hello

```






