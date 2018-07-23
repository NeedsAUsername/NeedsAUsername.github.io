---
layout: post
title:      "iteration confusion"
date:       2018-07-02 13:11:16 -0400
permalink:  brain_cells_each_cell_puts_im_confused
---


						 



The concept of looping and iterating was not foreign to me. I had first encountered it in Python, and it was as simple as 
"for i in x: [*do something*]". In javascript, things became a little messier, but the format remained the same. 
"for (*conditions*) {*do something*}. In Ruby, there is nothing called the "for loop". Rather, iterations are available through enumerables, and I was utterly confused with the concepts of ".each do |x|" and blocks, until I realized they did the same thing as for loops in Python and Javascript. Here I was, thinking that .each was something entirely new when it was really something I already knew, but was just in a completely different syntax. Even then, it was hard to adjust to the new way of writing loops in Ruby because the syntax was conceptually different, and I had to learn the two ways of writing it (through do/end and through using curly braces). And to further complicate things, I had to use .each_with_index to even be able to reference the index within the block. I also had to learn the return values of .each, and in came .collect to make things more interesting. All of this seemed to unnecessarily complicated the basic for loop that I had been so familiar with, but after adjusting to Ruby's enumerables, I also came to appreciate the powerful tools that came along with it.  

