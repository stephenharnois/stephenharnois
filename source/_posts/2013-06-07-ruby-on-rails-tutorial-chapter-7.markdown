---
layout: post
title: "Ruby on Rails Tutorial: Chapter 7"
date: 2013-06-07 15:37
comments: false
categories: ['Training', 'Tutorial']
---

Chapter 7 was about allowing users to signup for access to the application.
The three steps to get the signup function working is creating the form, handle signup failure and handling signup success.

<!-- more -->

##Signup Form
The form_for structure is used to create the form fields for user signup.
Every field is given a label and a field type.
There is also a submit function which creates the submit button used to send the filled data to the system to be evaluated.
The form_for takes an instance variable relating to the controller that it sends its data to.
Because the tutorial is using the bootstrap framework it is very easy to style the submit button.
You just have to add a few classes to the button and it is styled nicely.

##Signup Failure
When the signup fails the controller re-routes you back to the signup page and displays an error.
To display the errors an array attached to the user instance variable.
To display the errors we loop through the errors and print each on in an ordered list.

##Signup Success
Once the user signs in successfully you want to point him to the main profile page.
The new feature in this section is the use of the flash variable.
The flash variable is used to display a message on different pages than the one you logged in on.
Since the flash is a hash we can use the key as a css class for styling and use the value as the message to the user.

That is it for this chapter up next is Chapter 8.
