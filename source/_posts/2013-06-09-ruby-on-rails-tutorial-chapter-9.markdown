---
layout: post
title: "Ruby on Rails Tutorial: Chapter 9"
date: 2013-06-09 15:27
comments: false
categories: ['Training', 'Tutorial']
---
This Chapter is all about manipulating users and what they are allowed to do on the system.
The topics covered in this Chapter were updating users, authorization, showing all users on the system and deleting users.

<!-- more -->

##Updating Users
Editing users is very similar to creating new users, we just have to call the update cation instead of the new action.
We can use the find method to get the user id from the params structure and search the database for that user.
If there is a problem with the edit send the use back and display error.
On a successful edit just go to the users profile page.
This section was very similar to the work from the previous chapter.

##Authorization
The first step is to check if the user is signed in on every page and if not redirect them to the signin page.
We will also display a notice to the user to sign in.
I like how Rails uses the before filters in the controller to verify the correct user is signed in.
    before_filter :signed_in_user, only: [:edit, :update]
    before_filter :correct_user,   only: [:edit, :update]
The next interesting piece was a way to remember what page the user was looking for and forward them to that page once signed in.

##Showing All Users
The next step is to create a page to list all of the users, but we only want to show the users if a current user is signed in first.
We then grab all of the users from the database and display them on the page.
However this can cause a problem when the site grows ad has thousands of users.
The solution is to use pagination, which is to only grab a page worth of users from the database.
Then if you want to see more users you can request the next page of users.
The tutorial uses [will_paginate](https://github.com/mislav/will_paginate/wiki) gem to handle pagination.
Since the user view will be getting its data from the users controller you can add pagination simply by adding the following:
    :In the View
    <%= will_paginate %>

    :In the controller
    @users = User.paginate(page: params[:page])

##Deleting Users
The final piece of the puzzle is to allow admin users to remove users from the system.
We have to add a field to the users database that defines an administrative user.
Then we go to the list of all users and add a field to delete all users that are not the current user.
The actual removal is simple, just by calling the destroy method on the user and then return an acknowledgement to the user.

Thats it for Chapter 9 up next is Chapter 10.
