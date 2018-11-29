---
layout: post
title:      "innerHTML vs createElement/appendChild"
date:       2018-11-29 19:39:57 +0000
permalink:  innerhtml_vs_createelement_appendchild
---


<p>We can add elements to a DOM element by creating an element and appending it. (Let's pretend we have an exisiting div element to work with)
</p>


```
let newElement = document.createElement('p'); 
newElement.textContent = 'New Element'; 
div.appendChild(newElement); 
```

<p>We can also manipulate an element's HTML directly using innerHTML.</p>

```
div.innerHTML += '<p>New Element</p>' 
```

Using innerHTML is cleaner, especially when we start adding in extra properties like classes and javascript events. 

```
div.innerHTML += '<p class="paragraph" onclick="doSomething()">New Element</p>' 
```

<p>While clean, using innerHTML reparses and recreates all DOM nodes inside the div element and is less efficient than simply appending a new element to the div. In the above cases, createElement is the more performant choice, even if it requires more typing. 
</p>

However, innerHTML does have an advantage when we want to do multiple things to an element. For example, let's say we have to append a hundred lists to our div. 

```
for (i = 0; i < 100; i++) {
  let newElement = document.createElement('p'); 
  newElement.textContent = 'New Element Number: ' + i; 
  div.appendChild(newElement); 
}
```
If we use createElement, we must append on each iteration, resulting in a recalculation of styles, painting and layout every single time. This is hardly efficient, and using innerHTML within the loop the same way is even worse - but what if we add the paragraph htmls to a variable instead, and then only need to set the innerHTML one time at the end?

```
let newElements = ''; 

for (i = 0; i < 100; i++) {
  newElements += `<p>New Element Number: ${i}</p>`
} 

div.innerHTML =+ newElements;
```

As we can see, in simple one-time cases, createElement/appendChild is more efficient, but in cases where many changes are made, innerHTML is the more efficient choice.


