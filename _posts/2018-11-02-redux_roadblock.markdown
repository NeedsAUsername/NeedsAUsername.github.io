---
layout: post
title:      "Redux Roadblock"
date:       2018-11-03 02:59:04 +0000
permalink:  redux_roadblock
---


<p> Throughout my bootcamp experience, there is nothing that has confused and frustrated me more than Redux. This is especially weird because I understand the concept of Redux. As a React app grows, you create more and more components, each with their own state. It becomes hard to manage and keep track of every state, so in comes Redux with the solution of a store with all the states conveniently stored inside of it. Just connect a component to the Redux store to grant it access to any necessary state info. To change state, redux implements reducers, which takes in an action object, and spits out a new state. 
</p>
The idea is really nice: Simplify state into one store. To change state, dispatch actions to reducers. That's all. But the implementation feels so much more complicated than it needs to be. The connect function is hard to understand, and I don't quite get how to write mapDispatchToProps functions. Then there's the added folder structure of housing reducers and actions, not to mention the additional imports required, including createStore and Provider. 
</p>

<p> 
In contrast, React was absolutely lovely to learn. The concept was amazing, and so was the implementation; simple, and intuitive. There was nothing overly complex about components, props, or states. All you needed to do to set state was declare a state object, and all you needed to do to change it was pass an object into the setState function. 
</p>

<p>Frankly, Redux is just plain unenjoyable to learn. It's the first time that I've been so offput with how something is implemented. Throughout my coding journey, from learning Rails to Javascript to CSS, every part came with roadblocks where I struggled to understand concepts or syntax. But the process of learning them was enjoyable. I was always excited when my mind clicked, and I got a concept to work. Maybe Redux just hasn't clicked for me yet. </p>


