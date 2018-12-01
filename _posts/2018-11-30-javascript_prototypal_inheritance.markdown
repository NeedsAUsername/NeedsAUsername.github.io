---
layout: post
title:      "Javascript Prototypes"
date:       2018-11-30 22:54:00 -0500
permalink:  javascript_prototypal_inheritance
---


<p>All Javascript functions will have a prototype property. Let's take a look. 
</p>

```
function Example(){ return 2} 

Example.prototype // {constructor: ƒ}   

Example.protoype.name = 'An example' 
Example.prototype // {name: 'An example', constructor: ƒ}  
Example.name // 'An example'
```
<p>
Conversely, all objects have a __proto__ property, and *it will point to the prototype of their constructor function*  
</p>

```
let exampleOne = new Example 
exampleOne // {}
exampleOne.__proto__ // {name: 'An example', constructor: ƒ} 
exampleOne.name // 'An example'
```

<p>
This is an important revelation! exampleOne itself is an **empty object**, but its __proto__ is able to point to the prototype object! When exampleOne.name is called, Javascript first checks to see if exampleOne has a property called name. It does not, so Javascript will look at its __proto__ object for the name property, which it finds! 
<p>
Using prototype, Javascript objects *do not directly inherit properties from constructor functions. They merely have access to the prototype object of their constructor function.* 
</p>
This is why we can create an object, add a new property to the function's prototype, and the object will have access to it; of course, this would make sense now that we know the object's __proto__ property points to that prototype object, but it would seem like magic otherwise because this functionality cannot occur in classical inheritance. 
</p> 

<p>
To further prove out point, we can create another object from our example function and compare their __proto__ properties. 
</p>

```
let exampleTwo = new Example 

{name: 'not same obejct'} === {name: 'not same object'} // false

exampleTwo.__proto__ === exampleTwo.proto__ // true
```

<p>
The two __proto__ objects are equal, meaning they point to the *same object in memory*: the Example function's prototype. 

In fact, the function itself doesn't matter because it's not a class; only the prototype object matters. Let's prove that now. 
</p>

```
Example = 'Function Gone!' 
Example.prototype // undefined  

exampleOne.__proto__ // {name: 'An example', constructor: ƒ}
```

<p> 
We've altered the function, but the prototype object still exists in memory, so our objects still have a reference to it. 
</p>






