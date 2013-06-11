---
layout: post
title: "Ruby on Rails Tutorial: Chapter 6"
date: 2013-06-06 15:23
comments: false
categories: ['Training', 'Tutorial']
---

In Chapter 6 the topic was about how to represent a user in the system.
First was the user model then being sure you can validate that user and finally securing the users password.

<!-- more -->

##User Model
This section is about setting up user CRUD.
Which is how we interact with the database.
CRUD stands for create, read, update and destroy.
All of these functions are necessary for most structures that have a database backend.

##Validation
If you want to validate parts of the users information that is stored in the database.
Something similar to the following needs to be added in to the User model:

    validates :name,  presence: true, length: { maximum: 50 }
    VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i
    validates :email, presence: true, format: { with: VALID_EMAIL_REGEX }, uniqueness: true

The name and email symbols above can be replaced by any field that you need to verify information of.
The length field will verify the length, the format field makes sure the format matches, the presence verifies the field is filled in and the uniqueness verifies there is only one like that in the database.

##Password Security
Rails secures passwords very easily, you just have to add the following to the user model:
    has_secure_password
By using the code above the users password is turned into a cryptographic hash and that hash is stored in the database.
So even if someone gets a hold of the database all of the users passwords are still safe.

That is all for today tomorrow Chapter 7.
