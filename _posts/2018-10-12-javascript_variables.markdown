---
layout: post
title:      "Javascript Variables"
date:       2018-10-12 16:38:35 +0000
permalink:  javascript_variables
---


<p>In Javascript, variable declaration and variable assignment are seperated. When you declare a variable, with or without a value <code>var x;</code> or <code>var x = "a value";</code> it will return undefined. Only after referencing a variable declared with a value, or assigning it a value, will it return the value within the variable<code><pre>var x = "hey"; //undefined 
    x = "hello"; //"hello"</pre></code>. With 'var' and 'let', the declaration can be made without a value. With 'const', and declaring without a keyword, the declaration must come with a value. 
    </p>
    <p><code>x = 'hello';</code> is automatically a global declaration, must be declared with a value, and should be avoided.</p>
    <p><code>var x = "hello"; </code> can be global or local depending on where it is declared. Var variables can also be redeclared. This should be used sparingly.</p>
    <p><code>let x = 'hello';</code> is a block-scoped declaration. It can be assigned and resassigned a value, but not redeclared. Use this when you need to reassign the value of the variable.</p>
    <p><code>const x = 'hello';</code> must be declared with a value. It cannot be redeclared or reassigned. Use this in most cases.</p>
