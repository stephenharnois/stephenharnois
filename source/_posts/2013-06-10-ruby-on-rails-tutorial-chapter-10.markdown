---
layout: post
title: "Ruby on Rails Tutorial: Chapter 10"
date: 2013-06-10 15:57
comments: false
categories: ['Training', 'Tutorial']
---
This chapter was all about allowing the users ato enter their micro posts and to manipulate them.
The section are setting up the micropost model, displaying the microposts and then allowing the microposts to be manipulated by the user.

<!-- more -->

##Micropost Model
The microposts model is simple it only contains the actual post from the user and the user id of the user.
The main idea for this section is to setup a relationship between the user and his posts.
Since one use can have many posts and a post can only belong to a single user.
Rails allows you to set this relationship up very easily.
    :Micropost Model
    belongs_to :user

    :User Model
    has_many :microposts
Those few lines is all it takes for Rails to establish the relationship.
The last piece of setup for the micropost model is how to handle getting rid of users posts when the user is deleted from the system.
Rails has the following solution:
    :User Model
    has_many :microposts, dependent: :destroy
The dependent destroy option on the has many relationship will remove all associated posts when the user is deleted from the system.

##Displaying Microposts
The microposts will be displayed on the users profile page, so a section is added there to display the microposts.
To handle the pagination we will use the will_paginate ruby from the previous chapter with one small addition.
    <%= will_paginate @microposts %>
Since we are on the user view coming from the user controller we have to tell will_paginate that we want the micropost data to be paginated.
The last step to displaying microposts is a little bit of CSS styling and they are done.

##Manipulating Microposts
Now we have to add the CRUD elements to microposts just like they were for users.
Since now we now when a user is logged in we can check that on the home page and display a micropost form for users and a signup form for those who have not signed in yet.
Since the user and micropost have the relationship defined above we can do something clever and define the new micropost based on the current user, like so:
    @micropost = current_user.microposts.build if signed_in?
This one line will create a new micropost form for the user if they are signed in.
To destroy a micropost you just have to call the destroy method on the micropost.

Thats it for chapter 10 next is the final chapter 11 where users can follow other users.
