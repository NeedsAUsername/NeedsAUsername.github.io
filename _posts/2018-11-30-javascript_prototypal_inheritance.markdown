---
layout: post
title:      "Javascript Prototypal Inheritance"
date:       2018-12-01 03:53:59 +0000
permalink:  javascript_prototypal_inheritance
---


<p>Javascript has prototypal inheritance, instead of the classical inheritance found in most other languages. Classical inheritance lays out a blueprint for new instances to adopt, relying on commonalities between the instances. For example, creating dog and cat instances using an animal class. In Javascript, there are no classes. Rather, objects can simply inherit properties of other objects. But, you might be asking yourself, aren't objects created from functions? Yes, objects can be created from any function (the es6 class syntax is just sugar for constructor functions), but their properties are not inherited from the function itself, but from the prototype object that all functions have. Let's take a look. 
</p>

```
function Example(){ return 2} 

Example.prototype // {constructor: ƒ}   

Example.protoype.name = 'An example' 
Example.prototype // {name: 'An example', constructor: ƒ}   
```
<p>
Conversely, all objects have a __proto__ property, and *it will point to the prototype of their constructor function*  
</p>

```
let exampleOne = new Example 

exampleOne.__proto__ // {name: 'An example', constructor: ƒ}
```

<p>
This is an important revelation! Javascript objects *do not directly inherit properties from constructor functions. They merely have access to the prototype object of their constructor function.* This is why we can create an object, add a new property to the function's prototype, and the object will have access to it; of course, this would make sense now that we know the object's __proto__ property points to that prototype object, but it would seem like magic otherwise because this functionality cannot occur in classical inheritance. 
</p> 

<p>
To further prove that objects don't directly obtain their own properties, and that all objects created from constructor function merely have access to the prototype of the function, we can create another object from our example function and compare their __proto__ properties. 
</p>

```
let exampleTwo = new Example 

{name: 'not same obejct'} === {name: 'not same object'} // false

exampleTwo.__proto__ === exampleTwo.proto__ // true
```

<p>
The two __proto__ objects are equal, meaning they point to the *same object in memory*: the Example function's prototype. 

In fact, the function itself doesn't matter because it's not a class; only the prototype object matters. Let's prove that now. 

Example = 'Gone!' 
Example.prototype // undefined  

exampleOne.__proto__ // {name: 'An example', constructor: ƒ}
</p>

<p> 
We've altered the function, but the prototype object still exists in memory, so our objects still have a reference to it. 
This is what we mean by objects inheriting from other objects. Hopefully, prototypal inheritance in Javascript is a little clearer now! 
</p>




