---
layout: post
title:      "SASS basics"
date:       2018-12-30 05:10:36 +0000
permalink:  sass_basics
---

Sass gives us some pretty nifty functionalities in writing CSS. If you have Node installed, installing SASS is as easy as running `npm install -g sass`. Otherwise, check out the other installation methods at https://sass-lang.com/install. Once we have Sass installed, let's create an index.html to style. 

```
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title>Testing</title>
    <link rel="stylesheet" href="index.css">
  </head>
  <body>
    <div class="main">
      <h1>Hello World!</h1>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
      </p>
    </div>
  </body>
</html>
```

Next, let's create an index.scss file to see what we can do with sass(note that we need the file extension to be .scss to use sass).  First, we are able to nest children within parent code. 

```
.main {
  h1 {
    color: red;
  } 
	p {
	 color: blue;
	}
}
``` 

To compile this to a regular css file, we run `sass index.scss index.css`, where the first argument is our sass file and the second argument is our target css file. We can see that sass successfully compiles to normal css within the index.css file.

``` 
.main h1 {
 color: red;
}
.main p {
 color: blue; 
}
```

We can also set and reference variables with the $ sign. This is useful if you're using hex codes for colors. 

```
$lightRed: #ff8080;  
$darkBlue: #004080;
.main {
  h1 {
    color: $lightRed;
  } 
	p {
	 color: $darkBlue;
	}
}
```

Not only can we set variables, we can also set entire templates that allow for inheritance using % and @extend! 

```
$lightRed: #ff8080;
$darkBlue: #004080;

%lightRedColor {
  color: $lightRed;
}

%darkBlueColor {
  color: $darkBlue;
}

.main {
  h1 {
    @extend %lightRedColor;
  }
  p {
    @extend %darkBlueColor;
  }
}
``` 

This will compile to the same css as the last one. Although clearly not needed in this example, you can see how this would be much more useful in cases where you are reusing multiple lines of code!


