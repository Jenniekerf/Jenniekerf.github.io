---
layout: post
title:      "Adding Javascript to Rails"
date:       2019-09-22 21:08:31 +0000
permalink:  adding_javascript_to_rails
---


For this project we were asked to add Javascript to our already existing Rails project. I feel like the hardest part with Javascript so far is that there are so many different ways to do the same things. To keep track and remember them all feels impossible and I still don’t really know what method is best to use when. 
Because of that, starting this project felt a bit overwhelming. I ended up watching endless of videos to try to get some kind of idea on how to even start. The videos were a really big help! Watching someone go through the process over and over again eventually gave me some understanding on how everything is connected and how to apply it to my own project.

One requirement was to use Serializers. What a serializer does is basically that it takes code written in the backend and translates it so that it can be used in the frontend without having to write a bunch of code. Adding a serializer is easy. You just put “rails g serializer” followed by the name of the serializer in the console and it’s created for you. You then add the attributes and relationships you want to use and that’s it! Since I wasn’t sure what I’d end up needing I added one serializer for every model I have, all attributes and all relationships. I might remove some of it eventually since I don’t think it’ll be necessary to have all information available everywhere in my app.

Here’s an example of one of my serializers:

```
class BottleSerializer < ActiveModel::Serializer
  attributes :id, :name, :variety, :producer, :category, :year, :price_cents, :price_currency
  belongs_to :user
  has_many :comments
  has_many :commentors, through: :comments, source: :commentor
end

```


Next you have to change your controller to return data as json so that we then can use it in our Javascript file. This is also pretty straightforward. For example you change:

```
def create
    @bottle = current_user.bottles.build(bottle_params)

    @bottle = current_user.bottles.build(bottle_params)
    
    if @bottle.save
      redirect_to bottles_home_path
    else
      render 'new'
      end
  end
```


To this:

```
def create
    @bottle = current_user.bottles.build(bottle_params)

    if @bottle.save
      render json: @bottle, status: 201
    else
      render json: @bottle, status: :bad_request
    end

  end
```


After that is done you can start creating your Javascript file and filling it with the functions you need. We had to render various information without having the page refresh every time like it did using only Rails. This is the function I wrote to get all the bottles that belong to the current user:

```
function getBottles() {
  clearForm();
 let main = document.getElementById('main');
 main.innerHTML = '<ul>';
 fetch( '/bottles/home_index')
 .then(resp => resp.json())
 .then(bottles => {
   main.innerHTML += bottles.map(bottle =>
   {const btl = new Bottle(bottle)
   return btl.renderBottles()}).join('')
   main.innerHTML += '</ul>'

 })
```


On the first line I’m just declaring a function called “getBottles”. I’m then collection all data and set the variable “main” to equal “document.getElementById('main')” and then grabbing all inner HTML from the data by calling “main.HTML”. I get this data by making a fetch request to the URL “/bottles/home_index”, and when I get a response from that URL l I turn the data into json. To grab the bottles I  map over the inner HTML, grab the bottles and then call the “renderBottles” function that will display the bottles to my page.

I'll have to spend a lot more time learning Javscript before I will fully undestand it but this was definitely a step in the right direction!



