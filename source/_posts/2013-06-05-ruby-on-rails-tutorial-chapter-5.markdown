---
layout: post
title: "Ruby on Rails Tutorial: Chapter 5"
date: 2013-06-05 16:14
comments: false
categories: ['Training', 'Tutorial']
---

Chapter 5 was about filling in the layout of the static pages created in Chapter 3.
There were a lot of new ideas introduced in this chapter including CSS, Routes and controllers.

<!-- more -->

##Adding Some Structure
The main structure of the app is added using a CSS framework called [Bootstrap](http://twitter.github.io/bootstrap/).
This is my first time using it and I love the power it has to handle the structure by simply including a few classes in the HTML.

##The Asset Pipeline
The new version of rails uses an asset pipeline which streamlines the use of javascript, style sheets and images.
The coolest thing I learned was that with [Sass](http://sass-lang.com/) you can nest related CSS styles.
Which makes the style sheets easier to read and more compact.

##RESTful Routes
The final lesson of this chapter was the idea of RESTful routes.
An example is if you wanted to go to the about page of the example site it would look like this:
    www.example.com/about
In this process rails also assigns a name to the route:
    about_path
This makes the sites URLs clean and efficient.

That is all for today, tomorrow it is on to Chapter 6.
