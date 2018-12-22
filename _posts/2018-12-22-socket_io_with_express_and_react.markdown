---
layout: post
title:      "Socket.io with Express and React"
date:       2018-12-22 11:28:34 -0500
permalink:  socket_io_with_express_and_react
---


Traditionally, a client sends an http request to a client and the client sends back information to the client. Http is stateless, so requests aren't aware of any previous requests. This means that if we wanted to check if something is updated(let's say, weather info from a weather API), we would need to continuouly send a request every 10 seconds or so to see if there is any updated data. There has to be a better way, right? In comes web sockets, allowing continous real-time communication between server and client. Let's try it out with Javascript's socket.io library. 

To add socket.io to a Node app, we add it to our package.json with `npm install socket.io`. Next, we need to pass our server to it. 

```
const express = require('express');
const server = express();

const http = require('http')
const socketServer = http.Server(server);
const io = require('socket.io')(socketServer); 
```

We can't directly pass the server from express() to io because socket.io does not know anything about Express. Instead, we need to make use of http to create a server and then pass that down to io. Next, we need socket.io to listen for a connection event, and to ask our server to start listening for requests on port 5000.
```
io.on('connection', (socket) => {
  console.log('Connected'); 
}
const PORT = process.env.PORT || 5000;
socketServer.listen(PORT, () => {console.log('Socket Server started on ' + PORT)}) 
```

Now let's go to our React client. We're going to create a button that will change the text inside an h1 element, and use socket.io to transmit that to all of our clients. To start, we need to cd into our React client folder, and run `npm install socket.io-client`. 
Next, let's add the following to our app.js. 

``` 
import socketIOClient from "socket.io-client";

const socket = socketIOClient('http://localhost:5000');
socket.on('change text', (text) => {
  let title = document.querySelector('.title'); 
	title.textContent = text;
})

class App extends Component { 
 changeText = (text) => {
  socket.emit('change text', text)
 }
 render() {
  return (
	 <div> 
	  <h1 className="title">Hello</h1> 
		<button onClick={() => this.changeText('bye')}>bye</button>
		<button onClick={() => this.changeText('hello again')}>hello again</button>
	 </div>
	)
 }
}
```

First, we've imported our socketIOClient, and connected to our socket Express server. Then we set it to listen to a change text event, in which it will take our title element and change the text to what the function's text argument. We've created a button that will pass 'bye' into our changeText function, which will emit a change text socket event. We just need to add some code to our Express server to get this all to work. 

```
io.on('connection', (socket) => {
  console.log('Connected');  
	io.on('change text', (text) => {
	 io.sockets.emit('change text', text)
	})
}
```

Now, when we click the bye button, we emit a 'change text' event, which our socket server is now listenting for. When the socket server notices the event, it will emit a 'change text' event to all client sockets. This means that if we have two browsers, both of them will receive the event! Try it out- open up two browsers and notice how the title element of both browsers change when we click a button on either browser. This is the basic pattern that you can expand upon to build more complex real-time apps with socket.io. 






