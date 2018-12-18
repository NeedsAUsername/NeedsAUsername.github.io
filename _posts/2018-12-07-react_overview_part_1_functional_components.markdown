---
layout: post
title:      "React Overview Part 1: Functional Components"
date:       2018-12-07 21:48:21 -0500
permalink:  react_overview_part_1_functional_components
---

<p>
React is used for creating dynamic user interfaces. At the core of React are its components. The dynamic aspect of React comes through its use of state and props within components: every time state or props is changed, React checks to see if its virtual DOM has changed; if so, it makes the necessary rerenders! Let's step back a bit, and start from the beginning. 
</p>
<p>React Components come in the form of either javascript functions or classes. Functional components don't have state and are usually just used to present information given to it. They're often called stateless/presentational/dumb components; they're easier to understand than class components so let's start with creating a simple functional component. 
</p>
```
const Hello = () => (
  <div>Hello World</div>
)

ReactDOM.render(
  <Hello />,
  document.getElementById('root')
)
```

<p>
Not too difficult, right? ReactDOM.render takes an element to display as its first argument, and the element to attach it to as the second argument. Note that the Hello component is using JSX, which will compile to React.createElement('div', {}, 'Hello World'). This is why JSX only allows us to have one top level element, because React.createElement can only take one element as an argument! This also applies to ReactDOM.render. Then how do we render multiple components? Just like how we referenced the Hello component in the render function, we can also reference components within other components! That's why you'll most likely see an App component being passed into ReactDOM.render, with the App component containing all the other components in the web app. 
</p>

```
const App = () => (
<div>
 <Hello />
 <Bye />
</div>
)
const Hello = () => (
  <div>Hello</div>
)
const Bye = () => (
  <div>Bye</div>
)

ReactDOM.render(
  <App />,
  document.getElementById('root')
)
```

Now we can render hello and bye in our app! But wait- if we wanted to render more words, wouldn't that mean we'd have to keep creating components? There has to be a better way - in comes props! Props are properties that we can pass into components. We do this through their component tags, just as if we were passing something like an id inside a normal html tag. 


```
const App = () => (
<div>
 <Say words="Hello" />
  <Say words="Bye" />
</div>
)
const Say = (props) => (
  <div>{props.words}</div>
)

ReactDOM.render(
  <App />,
  document.getElementById('root')
)
```

<p>
Our new Say component is given a props argument, and is able to reference it inside curly braces, which allow us to run Javascript inside of them. Neat! 
</p>





