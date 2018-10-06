---
layout: post
title:      "Bind is pretty neat"
date:       2018-10-06 04:37:50 +0000
permalink:  bind_is_pretty_neat
---


It's pretty cool that Javascript allows us to change the 'this' context of a function using 'bind'. 

Let's see this in action. 

First. create two people with different names. 

```
function Person (name) {
this.name = name;
this.sayName = function() {
return `Hi, I'm ${this.name}`;
}
}
const Jack = new Person('Jack'); 
const Jill = new Person('Jill');
```

Now, if we wanted their names we can call on them like so: 

```
Jack.sayName() // *'Hi, I'm Jack*
Jill.sayName() //*'Hi, I'm Jill*
```
With bind, Jack can impersonate Jill by using her 'this' instead of his own!

```
Jack.sayName.bind(Jill)() //*Hi, I'm Jill*
```
This might seem like just another way to write Jill.sayName() but the importance here is that we're calling the method through Jack, not Jill. We can change Jill's own function to something entirely different and this will still work. 
```
Jill.sayName = function () {
'How do I say my name again?' 
]
Jill.sayName() // *How do I say my name again?*
Jack.sayName.bind(Jill) //*Hi, I'm Jill*
```
As you can see, bind is a great way to let objects access functions that they don't have themselves, so that you don't need to contantly redefine functions for every object. Just another example of Javascript flexibility!
