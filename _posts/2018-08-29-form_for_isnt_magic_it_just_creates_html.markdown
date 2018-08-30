---
layout: post
title:      "form_for isn't magic; it just creates html!"
date:       2018-08-30 02:47:49 +0000
permalink:  form_for_isnt_magic_it_just_creates_html
---

One of the many ways in which Rails provides almost magic abstraction is in the form builder and helper methods. It almost seemed a bit to magical to me until I realized that there was nothing magical about it. At its core, form builders create html. Yes, it has access to the object, and can do amazing things because of it, but you can just as well write out your own HTML form and it will function exactly the same way, even if writing the html requires more lines of code. Since form_for is just an abstracted way of creating forms, it makes sense that I need to understand the actual HTML that it outputs. In fact, a good strategy to understanding forms is to first write out what you want in pure HTML. Nothing fancy,; you control every aspect and it is exactly what you want. Now that you have something that works, you can spend your time creating a rails version of the form, and you can easily check your work by comparing the HTML output of the form builder- once they match, your job is done!  
