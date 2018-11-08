---
layout: post
title:      "CORS Trouble and how to get around it!"
date:       2018-11-07 22:55:19 -0500
permalink:  cors_trouble_and_how_to_get_around_it
---


<p>Just finished an intense debugging session, and decided to write a blog post about it! I was trying to fetch data from the yelp api, when I received an error I had never encountered before: 'Fetch API cannot load . Response to preflight request doesn't pass access control check: No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://127.0.0.1:3000' is therefore not allowed access. The response had HTTP status code 501. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.' 
</p>

<p>
An hour of fiddling with the fetch headers, and searching stack overflow, I finally arrived at an answer. Apparently, the authorization header that the Yelp API required triggered something called a CORS pre-flight process, where the browser sends an OPTIONS request to the server to see if the fetch request is safe. The server is supposed to send back an Access-Control-Allow-Origin header. If that header is not sent back, the browser will not start the fetch request, and this was what was happening when I tried to fetch from the Yelp API. 
</p> 

<p>The solution was to use a CORS proxy. Luckily there's a really useful one [here](https://cors-anywhere.herokuapp.com/). All I needed to do was to prepend the yelp URL with the proxy url in the fetch request. The proxy simply added a Access-Control-Allow-Origin header to the server's response, and all was well! Whew. 
</p> 

<p> 
You can read more about how CORS works [here](http://).
</p>

