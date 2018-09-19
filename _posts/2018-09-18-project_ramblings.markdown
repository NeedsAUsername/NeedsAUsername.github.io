---
layout: post
title:      "Project Ramblings"
date:       2018-09-19 00:43:12 +0000
permalink:  project_ramblings
---

This is just a copy of my notes that I wrote while encoutering a design delimma during my rails project. Most of this might not make sense without more context, but for some background, standard exercises are pre-created exercise objects that users can add to their program object, meaning that all users share that standard exercise object. 


current issue:
I don't want users to edit standard exercises (for good reasons). However, when users create their program, they have the checkbox to include standard exercises, therefore including them into the program. However, as the website develops, I want to use the weight attribute for exercises and that is not compatible with standard exercises (because of course changes will apply to all users with that exercise as well as the feature programs). I also cannot proceed with users adopting featured programs because of this reason, as their changes to it will apply to everyone.

possible solutions?
create duplicates of standard exercises and duplicates of featured programs then turn the featured/standard attribute to false. This way, users can edit them however they want, and it will not affect other user's programs/exercises, or the featured programs/standard exercises, and I can fully use the jquery + cocoon nested forms features. This may be hard to implement for the standard exercise checkbox on the program creation page since they are directly connected to the standard exercises. I could duplicate all the standard exercises and have that be the data in the checkboxes, but the checkbox value is still the ID, meaning I would need to create all the duplicates on every creation page refresh, and that would create a lot of unnecessary data for the database. Another idea is, instead of the checkbox value being ID, maybe pass in attributes and create a new exercise with those attributes? Can I pass in the object itself, then duplicate it?
Another idea could be to scrap the idea of the exercise having weights in the first place. Instead, I could have the journal track the weights instead, perhaps using the last entry's data. That way, I don't have to worry about duplication, and can keep the standard exercises attached to the user since users won't be making attribute changes to them. I would also be able to track users based on exercises since they all have the same program object. If I make duplicates, that is no longer possible. However, my programs themselves are already duplicates, sooo?


Aftermath: 
I ended up going with just having exercises be duplicated for every user so that they can edit/delete the duplicate without any repurcusions to the rest of the website. In hindsight, this was clearly the way to go, but I didn't know how to do it easily back then, so this whole brainstorm was essentially result of me trying to avoid writing that code. Reading through this, it's interesting to see how many ideas I could come up with to approach this issue. There's always more than one way to solve a problem, and even if one way seems the best, it doesn't hurt to brainstorm because you get a deeper understanding of what you really want to do. 
