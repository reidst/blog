---
layout: post
author: "Katherine Reid"
title:  "Goodbye, VBA"
date:   2023-07-26 11:07:12 -0500
categories: dts
---
Good news: we're not using VBA anymore! Bad news: I wasted a week of my life working on a project that was doomed from the start. Oh well - science is about disproving, not proving, and it is called "Computer _Science_" after all.

I don't feel too bad about it because the solution we finally settled on is so much better: a Flutter web app, hosted via GitHub Pages on a DiscoTrayStudios repo, where the Hendrix Today editors can log in and view the database or make updates/additions by uploading an Excel sheet with (mostly) the same format as the Excel sheet output by the submission form. This solution works so much better for several reasons:

1. The existing Firebase SDK for Flutter/Dart is feature-rich and very well supported (compared to the non-existent VBA Firebase SDK).
2. A web app tool meshes nicely with the original Hendrix Today editing workflow. Before copying each Excel row into Word for formatting, they can copy all the necessary rows into a temporary Excel book; after writing the email, they can add the HTML links to the descriptions in the temporary book via one of the many websites on the internet that can do that, then finally upload it to the web app.
3. Having the tool deployed from a DiscoTrayStudios repo makes maintenance infinitely easier than having it in an embedded script within a file on Sharepoint/Teams. We can also provide better user-facing errors, instructions, and warnings.
4. VBA is a messed up language lol

I started working on this Hendrix Today Uploader app on the 17th, and I basically finished it yesterday. I'm quite proud of the work I've put into it in that time, which includes an automated deployment pipeline via GitHub Actions that gets the latest pushes to the `main` branch, runs `flutter build`, and pushes the build to the `gh-pages` branch to be hosted; an Excel table viewer with 2D scrolling (not a task as easy as it sounds); Firebase email/password authentication and security rules that only allow the Communications account to write to the database; and multiple error messages that could help the editors fix potential issues with the upload file. The only thing that's missing is a way to delete items in the database, which I might add later this week.

For the user-facing app, Dr. Goadrich found a way to include it in the school's Azure Active Directory and added an official Microsoft login that only allows users with a Hendrix account to log in! With that, it's almost ready for beta testing this fall. All that's left is to add some sort of alert system that differentiates new items the user hasn't yet seen and a system to automatically delete outdated items (events that have passed and annoucements that have finished running).

To be honest, I'm very ready to be finished working on Hendrix Today. It's been fun, and I'm glad I was able to give it the love and care we did, but I signed up to this job to work on more than just one app, and I would feel bad if I ended up spending all summer giving all my attention to just one. Also, the fact that the only app I have worked on is the one for the school itself - the school I attend and the entity that is paying my stipend - feels unfair, albeit funny. Olivia is back in town and is working on the water quality testing app and Teddy is working on the computer vision backend for it, and I'm over here building an auxiliary Hendrix Today app to assist the primary Hendrix Today app.

It's hard to believe we only have a week of work left, but I'll make darn sure I spend at least some of that week on a different project!
