---
layout: post
title:      "Javascript Objects and Class Sugar"
date:       2018-10-17 03:10:40 +0000
permalink:  javascript_objects_and_class_sugar
---

    <p>Let's say that we had three people, and want to represent them in Javascript. Our code would get clunky very quickly if we just used variables.
		</p>
   
```
let Bob = 'Bob';
let Mary = 'Mary';
let Sue = 'Sue';
```

    <p>Instead we can use objects with a key(in JS all keys are strings) and a value.</p>
		
```
const people = {
Mary: 'Mary',
Bob: 'Bob',
Sue: 'Sue'
}
people['Mary']; //Mary
```
    <p>That's a little neater, and it more closely represents the idea that we want to portray. However, what if we wanted to include other attributes as well, such as age or height? Also, having the call a person by typing people['name'] is a hassle. Just a simple object won't be enough for this task. If you're coming from another language, you're probably thinking of a class. Let's take a look.</p>


```
      class Person {
        constructor(name, age) {
          this.name = name; 
          this.age = age;
        }
      }
```


   <p> The constructor tells us what parameters to use when declaring a new instance of a class. This may feel familiar to you if you're coming from another language, but there are no classes in Javascript. The class syntax in Javascript is pure sugar. It's really just a function.</p>
      function person(name, age) {
        this.name = name; 
        this.age = age;
      }  
    </code>
    <p>While this works, it is standard practice to capitalize the function name of object constructors. Now, we can easily create instances of objects without having to write them out manually.</p>

```
      const bob = Person.new('Bob', 20); 
      bob; // Person {name: 'Bob', age: 20}
      bob.name; // 'Bob'
      bob.age; // 20
```

    <p>Now this is the representation of a person that we were looking for! Note that while classes are just glorified functions, they are not hoisted like normal functions are. This means you can't create a new object before you declare the class. </p>
