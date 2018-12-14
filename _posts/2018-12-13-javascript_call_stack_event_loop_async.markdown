---
layout: post
title:      "Javascript Call Stack/Event Loop/Async "
date:       2018-12-14 00:15:23 +0000
permalink:  javascript_call_stack_event_loop_async
---

<p>
Think of the Javascript Call Stack as a list of function todos. Like the name implies, it functions as a stack, where functions waiting to be executed are stacked on top of each other, and are taken off starting from the top (last in, first out). More specifically, functions are entered into the stack when they are called, and taken off the stack once they return a value. Chrome developer tools enables us to see the stack in the source tab, and it is a great way to debug code because you can see exactly what functions are being called, the arguments they are taking in,  and their line of code. Let's take a look. 
</p>

```
function hello() {
 return 'hello';
} 

function talk() {
 return hello(); 
}

talk();
```

<p>
When talk() is called, the function talk is added to the call stack, and executed. The function hello is called from within the talk function, and thus it too is added to the call stack. The call stack now looks like this: main => talk => hello, where main is node's wrapper function (think of it as our program itself; when main is added, our program has started). Nothing more is added to the call stack, and it begins to unwind. Hello returns 'hello', and is removed from the call stack. Talk returns 'hello', and is also removed from the stack. There is no more code after talk(), and thus main is removed from the stack, signaling the end of our program. 
</p> 
<p>
When we run normal synchronous code, everything is done through the call stack, and functions are called in a blocking manner. Think back to the stack. We can't execute a function that's not on top of the stack, thus every function below it must wait one by one for the next function to be removed. Asynchronous functions, however, will allow synchronous code to run while it waits its turn(oftentimes, waiting for data from api calls). This leads to a performance boost, and is one of the benefits of building a program with Node, because Node often utilizes many asynchronous code. How does this work exactly?
</p>

```
async function fetchSomeData() {
 console.log('data fetched');
} 
function hello() {
 console.log('Hello') 
}

fetchSomeData();
hello()
```
<p>
If we run this code, 'I don't need to wait' is logged before 'data fetched', even though fetchSomeData was called before it. Let's dive into the call stack to see what is happening. fetchSomeData is sent into the call stack. However, it is asynchronous, so it will actually be removed from the call stack and sent to a thread pool, where it will wait patiently for its data to arrive. When the data is fetched, it is moved to the event queue. Meanwhile, this frees up the call stack, and our code continues to run. Hello is then added to the call stack, it prints 'hello' to the console, returns undefined, and is removed from the call stack. Normally, main would now be removed from the stack since there's no more lines of code in our program. But we still have fetchSomeData waiting in the event queue. When only main remains in the call stack, Node will check the event queue, and add them to the call stack. Thus fetchSomeData finishes executing, and data fetched is printed to the console. This cycle of bringing asynchronous code to the queue, and then back to the call-stack is Javascript's event loop.
</p>

