---
layout: post
title:      "React Overview Part 2- State"
date:       2018-12-22 02:26:52 +0000
permalink:  react_overview_part_2-_state
---


React is used for creating dynamic user interfaces. At the core of React are its components. The dynamic aspect of React comes through its use of state and props within components: every time state or props is changed, React checks to see if its virtual DOM has changed; if so, it makes the necessary rerenders! We went over functional components last time, so let's dive into their counterpart: class components and their use of state. 

Class/smart/stateful components are different from functional components in their use of state(whether it be their own state, or a global state from Redux/Mobx/etc. Unlike props, which belong to a parent component, state belongs to the component and only the component is able to make changes to it, just like only the parent component is able to make changes to the props it passes down. Class components are also able to make use of methods in the component lifecycle, but let's focus on its use of state in this lesson. 

```
import React from 'react'; 

class Form extends React.Component { 
 state = {
  name=""
 }
 render() {
	return (
	 <form>   
	  <label htmlFor="name">Name</label>
	  <input type="text" id="name" name="name" value={this.state.name} />
	  <input type="submit"/>
	 </form>
	)
 }
}
```

We've created a class component called Form, that renders a form with a textbox for a name. Since "for" is a reserved keyword, we used "htmlFor" instead. We are setting the component's state, which is just a Javascript object, and also setting the form's input value to the state. If we run this right now, we'll discover that we can't actually type anything into the box because it's set to the value of this.state.name, which is just an empty string. We need an event action that will take any changes we make in the form, and update our state.  




