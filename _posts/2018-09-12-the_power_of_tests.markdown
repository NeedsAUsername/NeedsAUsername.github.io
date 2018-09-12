---
layout: post
title:      "The power of tests"
date:       2018-09-12 14:05:12 -0400
permalink:  the_power_of_tests
---


When I started my rails project app, I was determined to write tests for it. Of course, I had experience reading and passing tests throughout the Flatiron labs, but writing tests for an entire project was something I had never done before. I thought it would be easy at first; after all, rspec tests are pretty much readable in English. However, being able to read them did not mean I was prepared to write them because I didn't know any of the syntax off the top of my head. This led me down a rabbit hole of looking up how to actually create tests. Normal test methods were relatively easy to grasp; they just involved manipulating methods and comparing a result to an expected result. However, things like request and feature specs were much more complex because they weren't just testing methods, but the website functionality itself. As I continued to figure things out, and write more and more tests, I began to appreciate just how powerful and simplistic the tests really were with the power of capybara. Methods like click_link, or fill_in were clear and read in plain english. 
I had no tests in my last project, and I ran into a multitude of problems because of it (I go over them in my earlier blog post). This time around, there was no need to constantly manually check every website function when I introduced a new one or edited a previous one, because I could just run my tests and see what passed and what didn't. Writing the tests themselves also forced me to state my goals in a clear and concise manner, leading my actual programming sessions to be much more focused and organized. With all the benefits that tests have given me in my rails project, they are definitely something that I'll always be utilizing in the future!
