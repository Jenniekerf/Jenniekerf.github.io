---
layout: post
title:      "My Final Project"
date:       2019-11-21 18:55:03 +0000
permalink:  my_final_project
---


My final project at Flatiron school is to build an app that has a Ruby on Rails backend API and a React/Redux frontend. This project has turned out to be the toughest one and the most time consuming to finish. Not because I think React/Redux it’s the most difficult part of this course but more because I hold myself to higher standards now after ten months of learning.

The fun part about it was how easy the Rails part of the project felt! After struggling with Javascript and everything that involves I was a bit worried I’d have forgotten about Ruby on Rails but that was not the case. To be mentioned though is that the Rails backend required for this project was a fairly simple one. 

React/Redux is not as big of a struggle for me to grasp as JavaScript was. It makes more sense to me and I understand all the steps much better. The problem comes with remembering them when no one is there to explain, but I guess that comes with repetition. At some point it’ll stick I’m sure.

React is a JavaScript library that makes it easier building user interfaces.
Redux is also a Javascript library, most often used together with React to manage the state of the application. Here’s a link to a great blog explaining Redux:

http://www.matthewgerstman.com/tech/how-redux-works/

For my project I decided to build an application for lost and found pets. Users can list their lost pets or pets they’ve found that need to find their back home. I built a simple CRUD backend in Rails and then I built the frontend with React/Redux.

In my app users fill out a form, putting in all the info about their lost or found animal. We then send a fetch POST request to the Rails backend database. Rails sends a response back to the frontend with the requested data. We now have that object to display in our frontend however we prefer. In my case I have one index page that shows all added animals and then I have two links to see either “lost” or “found” animals. A user can update and delete animals as well.

This is my action to fetch all animals from the Rails index page:

```
export const getAnimals = () => {
  return dispatch => {

    fetch(`http://localhost:3001/animals`)
    .then(res => res.json())
    .then(animals => dispatch({
      type: 'FETCH_ANIMALS',
      payload: animals
    })
  );
 };
};
```


And this is the corresponding reducer:

```
export default (
  state = [],
  action) => {
  switch (action.type) {

    case 'FETCH_ANIMALS':
      return action.payload;

      default:
        return state;
    }
  }
```

A reducer specify how the application’s state changes in response to actions sent to the store.
Any action you’d like to have in your app, like the update or delete actions mentioned above, will have their own corresponding reducer function.

You also need components! I think of components as the React equivalent to a Rails view page. A component is a JavaScript class or function that accepts properties and returns an element that describes what the user interface should look like.

Here’s my Navbar component:

```
import React from 'react';
import { Link } from 'react-router-dom';

const Navbar = () => (

  <nav className="navbar navbar-default navbar-expand-sm navbar-dark bg-dark">
    <div  className="container">
      <div className="navbar-header">
<div className="navbar-brand">Paws On The Loose BK</div>
      </div>
    <ul  className="nav navbar-nav nav-fill w-100%">
      <li class="nav-link"><Link to="/">Home</Link></li>
      <li class="nav-link"><Link to="/animals">All Animals</Link></li>
      <li class="nav-link"><Link to="/animals/lost">Lost Animals</Link></li>
      <li class="nav-link"><Link to="/animals/found">Found Animals</Link></li>
      <li class="nav-link"><Link to="/animals/new">Add New Animal</Link></li>
    </ul>
  </div>
  </nav>

);


export default Navbar;

```


After all of that is done there’s only styling left. I still have a ton to learn when it comes to styling so I try to find websites I like and use parts of their CSS in ways that work with my project.

Even though I’m now submitting this as my final project I still have a lot more I’d like to add to this app. I have a feeling it’ll be a work in project for a while. 


