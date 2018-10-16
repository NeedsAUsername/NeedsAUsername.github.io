---
layout: post
title:      "Javascript Hoisting"
date:       2018-10-15 21:13:48 -0400
permalink:  javascript_hoisting
---


 <p>Javascript reads through your entire code, and then executes it line by line. With this two-stage process, functions and variables declared with 'var' are stored in memory for the execution stage. This is called hoisting.</p>
 
```
    console.log(x)
    var x = "this will print undefined to the console"
```
   <p>In this case, JS goes through the code, and stores x in memory, but does not assign it a value because assignment takes place during the execution stage. The execution stage starts line by line, and console.log(x) is run. At this point x is undefined, and therefore undefined will be printed to the console. This will work for 'var', but not for 'let' or 'const', because they are both declared and assigned during the execution stage. This is another reason to avoid using 'var', as it would not make sense to call or print a variable before you declare it. Furthermore, instead of getting an error the code would run as normal, with the 'undefined' value being used, and it can be hard to pinpoint this problem. </p>
    <p>However, with functions, we do want to make use of hoisting, because the entirety of the function is stored in memory, so instead of having just an undefined value, we are able to make full use of the function.</p>
```
    function makeDinner() {
        prepareFood();
        cookFood(); 
        cleanDishes();
      }
function prepareFood() {
      someCode;
      }
function cookFood() {
      someCode;
      }
function cleanDishes() {
      someCode;
      }
```
   <p>Hositing allows us to have this intuitive setup for our functions. Note that if you assign a function to a variable this will not work, as we discussed above.</p>
