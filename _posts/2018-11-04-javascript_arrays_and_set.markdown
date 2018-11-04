---
layout: post
title:      "Javascript Unique Elements and Range"
date:       2018-11-04 12:39:20 -0500
permalink:  javascript_arrays_and_set
---


In Ruby, getting unique elements from an array is as easy as [Array].uniq

`[1, 2, 2].uniq; // [1, 2]`

There's no uniq method in Javascript. However, Javascript does have a built-in object called Set, which stores unique values. To use it to obtain unique elements from an array, simply instantiate it, with the array as the argument. 

```
new Set( [1, 2, 2] );  // Set(2) {1, 2}
```

Note that this returns an instance of Set. This object is iterable, so we can convert it to an array with the set operator.

```
let uniqueElements = [ ...new Set( [1, 2, 2] ) ];  // [1, 2]
```

Javascript also doesn't have the convenient range method that languages like Ruby and Python have. Lodash is a javascript library that does provide a range method, but what if we wanted to use vanilla Javascript?

We can create an array with ordered integers within a range by combining Javascript's Array object and key method. Similar to Set, Array returns an object that we can convert to an array with the spread operator. By passing an integer, we can create an array with n elements. 

```
[ ...new Array(5)]  // [undefined, undefined, undefined, undefined, undefined] 
```

All these undefined values aren't helpful, but we can just grab their keys with the key method and suddenly we have an ordered range of numbers!  

```
[ ...new Array(5).keys() ]  // [0, 1, 2, 3, 4] 
```
 

To determine the starting range, we can just slice the resulting array. 

```
[ ...new Array(5).keys() ].slice(2)  // [2, 3, 4]
```

To step the range, we can use Javascript's filter method. 

```
[...new Array(10).keys()].filter(num => num % 2 === 0) // [0, 2, 4, 6, 8]
```

Sometimes the answer isn't always obvious. But there's always a way to get it done. 






