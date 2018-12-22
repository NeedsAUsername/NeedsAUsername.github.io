---
layout: post
title:      "Socket.io with Express and React"
date:       2018-12-22 16:28:33 +0000
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


