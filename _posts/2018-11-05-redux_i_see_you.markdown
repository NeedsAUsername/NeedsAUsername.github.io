---
layout: post
title:      "Redux, I see you"
date:       2018-11-05 22:01:11 +0000
permalink:  redux_i_see_you
---


<p>Ok. So I made a post venting about my redux frustrations. I still think its implementation in React is way more complex than it needs to be, but Redux is  finally starting to make sense to me. Redux is a library that houses the store, a single source of truth for your states. React-redux is a library that enables you to connect your components to that store, and *that* was what I was having trouble with. Without it, you'd have to manually pass in the store as props to every component that needed it, and that kind of defeats the point of having redux in the first place. So, let's look at the connect method, and see if we can make some sense out of it. You'll probably see this line of code at the bottom of a component: </p>


```
export default connect (mapStateToProps, mapDispatchToProps)(ComponentName) 
```

Connect takes in two arguments. Let's look at each of them. MapStateToProps takes in the state of the store as the argument. You can use it to return an object with name value pairs that will be passed into the components as props. 

```
* Store State: { people: [Max, Bob, Mary] }* 

const mapStateToProps = state => {
   return {people: state.people}
}
```

<p>mapStateToProps does exactly what its name implies. It maps the state of the store into the component's props! Our component now has a prop called people containing the array of Max, Bob, and Mary. Essentially, we've passed down the pieces of store state that we want the component to know about. </p> 


<p>mapDispatchToProps is a little bit more tricky. We need to know about reducers and actions first. With Redux, state is immutable. Every time we need to make a change, we are creating a new state, and that's what Redux reducers are for. Reducers take in two arguments: the accumulated state, similar to Javascript's reduce function, and an action object. This action object will have a type attribute, and the reducer will run an action depending on that type, usually with a switch/case statement. For each case, we return an object and that object will become the new store state! </p> 

<p>Without passing in mapDispatchToProps, connect provides the component with the dispatch function that is passed down to the component through props. This takes in an object that will be passed as an action to the reducer, where the store state will be changed accordingly. We usually call dispatch in event handlers.</p> 

```
* In Component * 
handleOnSubmit = () => {
   this.props.dispatch({
	    return {type: 'someType', action: someAction} 
	 })
}

* In Reducer * 

switch(action.type) {
   case 'someType' :
	    const newState = someAction(state);
      return { newState };
}
```

This works, but we're still referencing dispatch inside the component. We don't want our components to be reliant on Redux functions, and that's where mapDispatchToProps comes in. 

```
* In Component *
handleOnSubmit = () => {this.props.doSomeAction} 

* Outside Component*
const mapDispatchToProps = (dispatch) => {
   return { doSomeAction: argument => dispatch({type: 'someType', action: someAction})
}
```

<p> mapDispatchToProps takes in the dispatch function as an argument, and refactors it away so that we can now reference it as doSomeAction in our event handler, instead of using dispatch. Neat! </p>

<p>So, I'm starting to see the light. Redux has its place in React, but with all the set-up required, it's definitely not an auto-include.  Most of the time it's okay to just leave state management to components. Only when your application starts expanding, and component states become harder to track, does Redux become necessary. Not to mention, Redux Devtools is absolutely amazing for keeping track of state. Not only can you see your entire app's state, you also have snapshots of every single time state was changed!</p>




