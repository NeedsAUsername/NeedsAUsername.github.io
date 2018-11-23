---
layout: post
title:      "Ruby and Javascript - Scope, Variables, Functions"
date:       2018-11-23 00:52:40 +0000
permalink:  ruby_and_javascript_-_scope_variables_functions
---


There's quite a few differences in how scope, variables, and functions are treated in Ruby versus in Javascript. 

To start off, Javascript uses lexical scoping, meaning that inner functions/closures have access to outter functions further up its scope chain. 

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


Ruby methods, on the other hand, are closed off from information outside of the function. The only variables it has access to are the ones declared within the function, and those passed through in arguments.  


