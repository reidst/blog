---
layout: post
author: "Simon Reid"
title:  "Razor Pages"
date:   2023-10-16 21:47:43 -0500
categories: "340"
---
Our latest lab assignment in Databases and Web Systems involved creating an ASP.NET Core web app that would facilitate CRUD operations on a basic list of items of interest. Mine, which can be found [here](https://github.com/reidst/csci340lab7), catalogs a few of the more famous home computers of the 80's.

Overall, the process was somewhat confusing, but that is to be expected from a new framework. With time (working on our final project, meeting with Dr. Goadrich, watching YouTube tutorials), I'll get the hang of it. It feels like a powerful system; I really like the association of a C# class with each page, and while I'm not familiar with the code-model-to-database-schema associations, it seems to be one of ASP.NET's central features, so I'd like to hope it's a good system.

The tutorial itself was pretty easy - if it was followed to the letter. This can be said about practically any tutorial, but as soon as I wanted to do something slightly different, I'd run across errors the tutorial doesn't explain, and I'd be on my own to solve them. In particular, when it came time to test database migrations, I wanted to change a field type from `decimal` to `int`, but it resulted in some other type of error than the one the tutorial expected. I was able to solve it by deleting everything in the database and refilling it, but that's not the kind of solution that should be relied upon in a more official environment.

It bothers me when I'm completely in the dark about the inner workings of a system and still expected to use it, a bother that led me to spend over twice as much time as my classmates professionally banging my head against Flutter. I hope for the sake of my team partners and my future self that I can get over this bother with respect to ASP.NET, whether through acceptance of the unknown or lots and lots of tutorials.