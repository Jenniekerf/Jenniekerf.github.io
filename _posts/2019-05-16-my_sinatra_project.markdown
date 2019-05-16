---
layout: post
title:      "**My Sinatra Project!**"
date:       2019-05-16 23:24:29 +0000
permalink:  my_sinatra_project
---


For our second project assignment we had to create an application from scratch using Sinatra. It had to include a way for users to log in and log out safely, a way to create, read, update and destroy (CRUD) data once you’re logged in and to make sure no one can edit or delete data that is not yours. It also had to have a “has_many” and a “belongs_to” relationship between at least two models. 

**My project**
I chose to make a vegetable garden organizer to keep track of when and what was planted. Unfortunately I don’t have a garden right now but I long for the day when I can have one again. I grew up with a big garden and my mom still plants and harvest that garden every year. She has this little book where she writes down the dates and names of what she has planted but this book tends to get really messy so I thought I’d create a system for her and others to be able to keep track of their gardens in a more organized and modern way.

**Models**
I decided to have two models, a Gardener model and a Vegetable model. The Gardener has_many vegetables and the Vegetable belongs_to a gardener.

**Controllers**
I decided to have three controllers; one for each of my models and also an Application controller to keep all data that is not directly connected to either of the models. The Vegetable and Gardener controller are inheriting that info from the Application controller.

**RESTful routes**
A RESTful route is basically an unwritten rule about how to design and handle URLS to make data manipulation easy for everyone to follow. It’s like a bridge between HTTP verbs and CRUD actions, working almost like translater so that the user doesn’t have to worry about it.

**CRUD**
In order to implement CRUD we need to create controller actions or routes. 
You will need a “GET”, “POST”, “PATCH” or “DELETE” route to “request” an URL. 

Example:

```
get '/home' do
    erb :index
  end
```


This tells you that at the URL ending with ‘/home’ we will render the HTML info found in the erb file ‘/index’.

Let’s say that we in our ‘/index’ file we have a form for our users to fill in their username and password to log in. We now need to create a controller action to POST this info. 
For every new action there need to be a route making sure our HTML gets “translated” and that it ends up in the right URL.

For editing you would need a “PATCH” route.  The “DELETE” route is pretty much self-explaining. 

In my application you can look at all the vegetables that other people have planted if you’re not logged in. If you are logged in you can create, delete and edit a vegetable in your own garden.


**Obstacles and lessons learned:**
Working through the labs leading up to this project I was struggling with keeping my focus on one task at a time. Everything is connected in one way or the other and I found myself starting with one task and then suddenly doing ten different tasks at the same time. I had the same problem while working on this project and it left me very frustrated at times. I think that the hardest thing for me was not fully understanding the error messages that would come up. It’s hard to fix an error if you don’t understand where to look for it and since everything is connected I ended up trying to change everything at the same time which led to more errors and more confusion. I think my biggest lesson I learned from this project is to make sure you stay on your route and fix and complete one thing at a time. A second valuable lesson is that a second pair of eyes can sometimes save you hours of frustration!

