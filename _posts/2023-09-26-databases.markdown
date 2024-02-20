---
layout: post
author: "Katherine Reid"
title:  "Databases"
date:   2023-09-26 22:48:48 -0500
categories: "340"
---
Last week in CSCI 340 we started talking about databases and how to create an effective model based on a client's needs. We started with [Entity-Relationship Models](https://en.wikipedia.org/wiki/Entity%E2%80%93relationship_model) then modeled them using a tool called Vertabelo that lets a user graphically create tables and relationships and can convert the model into a SQL (or other database language) script. Our assignment for Lab 6 was to take the following scenario and design a database to meet the requests:

> Your local grocery store would like your help in creating an online grocery shopping web application. The owner of the store will be able to list items for sale, where the items have a name, price, description, quantity available, and a manufacturer. Customers will be able to go to the site and register to create an account, entering in their name, address, and phone number. Once registered, customers will be able to start an order for pickup or delivery. The customer can select from the food items the store has for sale. When an item is selected, the customer will note the quantity desired, any special instructions, and if this item can be substituted if the store is out of stock. Finally, when the customer finalizes their order, they will be able to choose a time and date for their order to be fulfilled. Finalized orders can no longer be changed by the customer.

To meet this specification, I created the following ER diagram:

![An entity-relationship diagram made to model the example client specification above.]({{site.baseurl}}/assets/images/csci340lab6erd.png)

I originally only had `Item`s and `User`s connected via the `Order` relationship, but I realized that manufacturers could be extracted into their own entity since several items can have the same manufacturer. Despite the manufacturer having a small attribute set, repeatedly listing strings of moderate length could become a source of input error.

This diagram translated to the following Vertabelo model:

![A SQL database model based on the ER diagram above.]({{site.baseurl}}/assets/images/csci340lab6sqlmodel.png)

The manufacturers-to-items relationship is a one-to-any relationship, since each item has exactly one manufacturer but a manufacturer doesn't necessarily have to have an item available in-store at the moment. Each order is associated one-to-one with an item being sold, and each user can make zero or more orders while each order is made by exactly one user.

I'm still not sure what the SQL analogue for lists is; I would have liked for each order to contain one or more items, but since that doesn't seem possible (it would be a many-to-many relationship, so in which table would the foreign key go?), I settled with a one-item-per-order system and figured that a multi-item order made on the frontend could be translated to several single-item orders in the background.

In my experience, the best way to learn is to fail several times over the course of several years until one day you magically "get it," which is hopeful in the sense that I _will_ eventually get the hang of database modeling but unnerving in the context of our impending final projects involving real databases and real clients. For now, I'll just try to run all my database-modeling decisions by Dr. Goadrich first, and take solace in every correction made!
