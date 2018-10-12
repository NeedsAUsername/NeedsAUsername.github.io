---
layout: post
title:      "APIs- read the documentation!"
date:       2018-10-12 01:36:55 +0000
permalink:  apis-_read_the_documentation
---


During my first portfolio project, a cli app for displaying stock info, I wanted to scrape trending stocks on the Stocktwits website. I couldn't grab the elements, so I looked up the api and found that it had the trending stocks info. I scraped the actual api website, and didn't think more about it. Little did I know, there is so much functionality built into apis, and I been on the tip of the iceberg with my basic html scraping. With javascript functions like fetch and Ruby gems like Faraday, accessing apis is simple. Well, sort of. All apis are different, and they all have different documentation. Some require access tokens, and getting them can be a bit confusing. The most important thing to do when coming across a new api is to thoroughly read through the api to make sure that you're passing in the necessary keys and values. It woud be great if accessing all APIs were as easy as fetching the needed url, but the extra security is necessary for convenient actions like sending a tweet or creating a github repository (after all, you wouldn't want anybody besides yourself to be able to make changes to your accounts, right?), and providing keys like client_id makes it easy for the API provider to track who is using their api. 
