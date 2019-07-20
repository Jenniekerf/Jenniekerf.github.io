---
layout: post
title:      "Wine-Cellar - My first Ruby on Rails Project"
date:       2019-07-20 16:32:03 +0000
permalink:  wine-cellar_-_my_first_ruby_on_rails_project
---


I created my first Rails Project and it feels great! Going through the labs leading up to the project I felt like I never really grasped one subject before we moved on to the next one. So much information and as soon as I learned a new thing I forgot something previously learned. 

With that in mind I felt a bit overwhelmed starting the project. I realized that it would take a lot of hours watching tutorials, endless googling and a lot of trials and errors to make this happen, and it did, The good thing about that is that I learned so much! Before, I felt like I didn’t quite understand how everything was connected; every lab covers one topic and then the next lab covers something else. By building this app I got a totally different understanding on how everything is connected. 

My project:
As I’m a big wine lover I decided to create an app that organizes your wine cellar or wine collection. It could also be used as a virtual wine cellar as a place to log wines you’ve tried and liked and would like to remember. 

I decided that you don’t have to be logged in to see all wines added to the app from different users but in order to add wines or tasting notes you have to be logged in. Once logged in you can visit your private cellar where you’ll find only the wines you’ve added. You can also delete and edit bottles in your own cellar. 

In the index view I also created a dropdown menu where you can choose to look only at specific wines sorted by either price or category using the Scope method on my Bottle model. 

I tried to keep it as simple as possible but still include all the required elements. I also tried really hard to focus on one thing at a time since that was something I was struggling with in the Sinatra project.

One of the things that I struggled with the most even before I started coding was to figure out the has_many_through relationships. I tried approaching it from all different angles but it still didn’t make sense. My modes are User, Bottle and Comment where Comment is the table joining Bottle and User. I finally figured it out when I learned about Aliasing Associations. Especially this video helped me a lot: https://instruction.learn.co/student/video_lectures#/33

This is how my table associations ended up:

USER
```
  has_many :bottles
  has_many :comments
  has_many :commented_bottles, through: :comments, source: :bottle

```
BOTTLE
```
  belongs_to :user
  has_many :comments
  has_many :commentors, through: :comments, source: :commentor
```
COMMENT
```
belongs_to :commentor,
             :class_name => "User",
             :foreign_key => "user_id", optional: true
 belongs_to :bottle
```




I also struggled a bit with the layout since my HTML and CSS skills are limited still. I ended up spending a lot of time trying to find CSS in other websites and apps that I could then implement into mine. Very time consuming when you’re not sure what you’re doing but the end result was worth it!


All and all I’m very happy with the outcome, I would totally use this app since I never remember what wines I like!



