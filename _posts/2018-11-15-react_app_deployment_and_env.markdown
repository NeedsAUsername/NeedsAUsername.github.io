---
layout: post
title:      "React app deployment and .env"
date:       2018-11-16 03:49:04 +0000
permalink:  react_app_deployment_and_env
---

<p>
I had deployed my React app to Heroku only to discover that my fetch requests were not working. I went through an hour long session of puzzlingly trying to figure out why this was happening. I looked up deployment tutorials, tried configurations, and buildpacks, but to no avail. Then I happened to notice in the network tab that my requests to my Rails API were going to the wrong url. I was then able to fix the problem in about five minutes, and I'm still not sure whether to be happy or upset that the fix was so simple.
</p>
<p> 
Let's start with some background info. Right out of the box, create-react-app lets you define environment variables in an .env file (much like the dot env gem does in Rails). The variable has to start with REACT_APP_, and you can access it using process.env.variableName. The .env file is great for holding things like API keys. I was using it to hold my rails api url, and my CORS proxy url. So my fetches included `${process.env.REACT_APP_RAILS_API}` in the url, and this worked just fine in development. 
</p>

<p>
Now onto Heroku, where the source of my problem was. When I deployed my site, the .env variables were no longer accessible, and returned undefined. So my fetches were basically going to something like 'undefined/users', and of course that wouldn't work. The solution is actually quite simple. 
</p>

```
*In terminal*
heroku config:set VARIABLE_NAME
```

<p>
...Yup. You can retrieve it with javascript, just like the .env variables, so there's no need to change any code. For added convenience, you can also access config vars in your heroku dashboard settings. 
</p>


