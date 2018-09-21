---
layout: post
title:      "Javascript For Loops"
date:       2018-09-20 18:56:16 -0400
permalink:  javascript_for_loops
---


Javascript for loops can incorporate different types of logic, depending on what variable you want it to respond to. 

const array = [1, 2, 3]

The standard for loop: very customizable.
for (let i = 0; i < array.length; i++) {
   console.log(array[i]);
}
//1
//2
//3

The for..in loop: a more elegant way to loop objects.
for (var i in array) {
  console.log(array[i]);
}
//1
//2
//3

The for..of loop: easy access to elements, similar to Python's for loop
for (var element of array) {
  console.log(element);
}
//1
//2
//3

Another note is that Javascript's for loops are destructive, whereas Ruby's .each method is not.  
