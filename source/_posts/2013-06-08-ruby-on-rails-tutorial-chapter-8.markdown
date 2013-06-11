---
layout: post
title: "Ruby on Rails Tutorial: Chapter 8"
date: 2013-06-08 15:48
comments: false
categories: ['Training', 'Tutorial'] 
---
Chapter 8 is about Signing the user in and out.
The three sections in this chapter was setting up sessions, handling signin failure and handling signin success.

<!-- more -->

##Sessions
Sessions are a semi-permanent connection between server and client.
Ruby uses cookies to store the session data.
When a user signs in a new session has to be created.
When a user signs out the existing session has to be created.
Ruby does this using routes to point to the correct function.

##Signin Failure
First a new signin page has to be created to setup the new session.
Once the user signs in their password is compared to the hash stored in the database.
I like the way that Ruby authenticates users.
    user && user.authenticate(params[:session][:password])
This solution is very elegant because if the user does not exist then user will be nil and it will stop comparing there.
If the user exists and the password is wrong then signin will fail.
The only way for the user login to succeed is if both user name and password match what is in the database.
The flash that we setup last chapter is used here again to alert of a failed signin attempt.
Once signin fails the user is redirected to signin again.

##Signin Success
Once the user signs in correctly we send them to the profile page.
To remember if a user has signed in we generate a random token and store that in there session.
I like the way Rails handles expiring cookies, normally cookies expire at some time.
If you want them to last a long time you would do the following:
    cookies.20.years.from_now
    cookies.premanent
These two statements will have the same effect, since Rails has added a special permanent method.
The current user is also stored in the session so that authorization can be handled.
The last thing to handle is destroying the session once the user logs out, which is done with the delete method of the cookie.

Thats it for this Chapter next is Chapter 9.

