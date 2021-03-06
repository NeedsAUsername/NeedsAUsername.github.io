---
layout: post
title:      "Javascript Variables"
date:       2018-10-12 12:38:35 -0400
permalink:  javascript_variables
---


<p>In Javascript, variable declaration(creating a variable) and variable assignment(giving a variable a value) are seperated, and declarations will always return undefined whether it comes with or without assignment.</p>
<code>var x; //undefined <br>
var x = "a value"//undefined;</code>. 
<p>Only after referencing a variable that has been assigned a value, or assigning it a value, will it return the value within the variable</p>
<code>var x = "hey"; //undefined  <br>
    x; //"hey"</code>. 
<p>With 'var' and 'let', the declaration can be made without assignment. With 'const', and declaring without a keyword, the declaration must come with assignment.</p>
 <code>x = 'hello';</code> is automatically a global declaration, must be declared with a value, and should be avoided.<br>
    <code>var x = "hello"; </code> can be global or local depending on where it is declared. Var variables can also be redeclared. This should be used sparingly. <br>
    <code>let x = 'hello';</code> is a block-scoped declaration. It can be assigned and resassigned a value, but not redeclared. Use this when you need to reassign the value of the variable. <br>
    <code>const x = 'hello';</code> must be declared with a value. It cannot be redeclared or reassigned. Use this in most cases.
