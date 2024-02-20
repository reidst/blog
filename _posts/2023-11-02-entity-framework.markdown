---
layout: post
author: "Katherine Reid"
title:  "Entity Framework"
date:   2023-11-02 15:19:52 -0500
categories: "340"
---
We did another ASP.NET tutorial lab this week, this time focusing on Entity Framework's ability to connect C# models to a database. The tutorial was very long and bland, simply asking the user to copy/paste code and terminal commands into the project and occasionally run the app to ensure correctness. Most of the tutorial - I would say at least half - just explains what all the pieces do, making it more a reference manual than a proper tutorial. I found the work very easy (the only errors I ran across were due to me not following the instructions) but incredibly dull. That being said, I will certainly be using it as a reference for my team's final project. It covers just about everything we could need out of it and describes the reasoning for much of it, going so far as to explain how to protect against overposting attacks and how to write efficient queries.

The only difficulty I noticed working with multiple tables was the amount of duplicated boilerplate code that was almost identical to the code from the previous ASP.NET lab but tweaked to display new information. This is partially due to the fact that each table had an entire webpage for each CRUD operation, which our final project will not have, but I do hope that the large number of hierarchical tables in our project won't balloon into massive amounts of code. I'm pretty confident that it won't; our tables should translate neatly to an object-oriented specification.
