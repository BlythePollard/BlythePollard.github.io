---
layout: post
title:      "Render Vs. Redirect"
date:       2020-03-11 13:59:24 -0400
permalink:  render_vs_redirect
---


The topic of rendering versus redirecting is one that has followed (read: "haunted") me through both my Sinatra and Rails projects. I've listened to Avi explain the difference multiple times on videos, I've re-read the same Medium article on the topic multiple times, I've gone into many long StackOverflow rabbit holes, and every time I gather the helpful information, I forget again 5 minutes later. 

During my Sinatra project assessment, Dustin and I spent time talking over the difference between rendering and redirecting, I wrote extensive notes, and...surprise, I promptly forgot. Moving into my Rails project, I found myself making the same mistakes, not differentiating well between the two rerouting methods, and not being able to explain when to use one over the other. Enough is enough! Let's get this figured out. 

First thing's first:

**What is render?**
* A render can be used to show a view, text, layout, or a number of other things. When we render a view (i.e. render '/users/new'), we are literally telling Rails what view page (or item specified) to use (the view called '/users/new'). Only one render can be used per controller method, and they're often used in an if/else statement as the action to be taken if the action is unsuccessful. Here's a key aspect of render: when we render, we don't lose access to any of the variables or params defined in that controller action. This means that when we render to an erb template, we are able to use those params.

**What is redirect_to?**
* Redirect_to also brings the user to a new page, but through a very different process. Redirect_to moves from one action to another through a URL request. When we use redirect_to, our code stops running and waits for the new request from the browser.  Unlike render, when we redirect_to, we put in a stateless HTTP request, meaning that any variables or params defined in the controller action are *not* carried over to the new URL that we redirect to, and the URL does not need to change or reload.

**What do they have in common?**
Well, render and redirect_to are two ways to end a controller action. They are used to specify the particular paths we want our controller actions to take. That said, they are not always necessary-- remember that Rails automatically renders properly-named templates with their corresponding controller actions using CRUD norms (the new method will render to the "new.html.erb," edit method will render "edit.html.erb," etc.), so we only need to specifically render or redirect when we'd like to customize these paths.

**Okay, so when should we render, and when should we redirect?**

Here's an easy rule of thumb: if you are going to need to carry variables defined in a controller action on the next page (to fill a form or show validations, for example), use render. Redirect_to is best used when you want to make an HTTP request to another action, either within your own app or to an external URL. Because redirect_to creates a new request, it operates more slowly than render, meaning that it's best to only use redirect_to only when it's the right tool for the job. 

***

Until I become more automatic with my understanding of when to use render and when to use redirect_to, I'm happy to have this resource to come back to as I develop my Rails skills. Hopefully someone else out there finds it useful as well!



