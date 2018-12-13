---
layout: post
title:      "Javascript Coercion"
date:       2018-10-22 17:30:43 -0400
permalink:  javascript_coercion
---

Javascript tries its best to ouput a result, when other languages would throw an error. This can be confusing for many newcomers to the language. Take, for example: 

```
'2' == 2 // true 
```

How can this return true when comparing a string to a number? This is where Javascript coercion comes into play. Javascript will try to match the two types in a way where it can successfully complete the operation. Javascript will coerce, or convert, the number 2 into a string type. We can see this clearly with the following: 

```
'2' + 2 // '22'
```

Javascript coerces the 2 into a string, and concatenates, resulting in '22'. In cases of addition and comparison where one variable is a string, the other will also be coerced into a string. However, in cases of multiplication or division the string will be coerced into a number, like so: 

```
'2' * 2 // 4
```

The string '2' is coerced into a number, and thus 4 is the result. 
But wait there's more. The same quirky coercion process works on booleans. Let's take a look. 

```
false == 0 //true 
true == 1 //true 
```

In Javascript, false coerces to 0, and true coerces to 1. You can see this coercion explicitly when you call Number or Boolean. 

```
Number(true) // 1 
Number(false) //0 
```

This can make for some interesting code that can be hard to debug. 

```
3 > 2 > 1  // false 
```

Imagine trying to debugging this without knowing about coercion!  Javascript's comparison operator moves from left to right. So it first compares 3 > 2, which is true. Then it compares true > 1. We know that true coerces to 1, so 1 > 1 is false. 

```
3 > 2 > 1 
// true > 1 
// false 
```
Crazy!  To get this operation to function properly, we need to insert an AND statement in between the operations. 

```
3 > 2 && 2 > 1 //true
```

Whew. As for the equality comparisons, we can simply use the triple comparison operator, which will check for type, and return false if the types are different. 

```
2 === '2' //false 
2 === 2 //true 
```

But what about the weird addition and subtraction?

```
let a = '1'; 
let b = 1; 

function add_same_types () {
   if (a === b) {
	    return a + b;
   }
	 else {return 'not the same type!'}
}

add_same_types(a, b) // 'not the same type!'
```

Javascript is unique in its coercion. Hopefully, being aware of it will spare you some frustration in your next debugging session!






