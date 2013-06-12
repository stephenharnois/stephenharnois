---
layout: post
title: "Ruby on Rails Tutorial: Chapter 11"
date: 2013-06-12 15:13
comments: false
categories: ['Training', 'Tutorial']
---
The final chapter of the tutorial is all about adding the ability to follow users.
The sections of the chapter are setting up the relationship model, creating a web interface for following users and setting up the status feed.

<!-- more -->

##Relationship Model
To setup the relationship between followers and the people they follow Rails has an interesting solution:
    has_many :followed_users, through: :relationships, source: :followed
This code sets up a relationship between users through the relationship table.
The user model then needs functions to determine if you are following a user and a function to setup a following relationship.
There also needs to be a way to destroy the relationship between users.
Since this relationship has been setup the reverse relationship can be collected from the table very easily.

##Web Interface
On the user profile there will be a number representing the people you are following and the people who follow you.
The first step is to add the following and followers routes to the routes file.
Then get the user and check the relationship table to find the followed and followers counts.
Next a button is added to each users feed to let you know if you are following that user.
If you are following them the button will say unfollow and if not following them then the button says follow.
The final piece is to add the gravatar images for each of the people you are following below the number of followers.

##Status Feed
The status feed needs to contain the list of all of your posts combined with the post of the people you are following.
The following is a blend of Rails, Ruby and SQL that will get the list of microposts to include in the status feed:
    followed_user_ids = "SELECT followed_id FROM relationships
                         WHERE follower_id = :user_id"
    where("user_id IN (#{followed_user_ids}) OR user_id = :user_id", user_id: user.id)
That finishes up the status feed section of the app.
This tutorial had time when it was difficult, but if you stick with it and read over the sections a few times I found that it clicked.

That is it for this tutorial next I will be moving on to the [Ruby Koans](http://rubykoans.com/) tutorial.
Ruby Koans uses ruby itself to teach the language.

