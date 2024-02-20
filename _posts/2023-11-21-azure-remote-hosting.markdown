---
layout: post
author: "Katherine Reid"
title:  "Azure Remote Hosting"
date:   2023-11-21 23:19:23 -0600
categories: "340"
---
We just completed the last lab assignment of the semester - deploying an ASP.NET website with a database backend to Azure. Overall, it was just another Microsoft tutorial, in which the hardest part is following the somewhat convoluted instructions. However, there were some unique obstacles we encountered, including but not limited to the sudden release of .NET 8.0 which messed with a lot of the CLI operations. Thankfully, this was fixed by inserting a `--version 7.0` into the affected `dotnet` commands. We also had a problem selecting the proper database engine (PostgreSQL rather than SQLAzure). I've been having enough trouble with incompatible database types myself outside the lab - I'm currently writing a Python script to translate our client's Access database into a more compatible SQLite format. Hopefully that project will mesh well with our Azure-deployed final project, because if it doesn't, it is entirely my responsibility to fix.

Since this lab was done as a group project, the repo is owned by one of my final project teammates, and we worked as a team through their computer during the appointed in-class work days and a late-night library study session. Originally, we tried distributing the work and forking the GitHub repo first, but this led to conflicts further down the line (Microsoft tutorial moment) and we eventually restarted and worked from a single person's computer. This made our development process a lot smoother.

Our deployed project can be found at [msdocs-core-sql-ayz.azurewebsites.net](https://msdocs-core-sql-ayz.azurewebsites.net/), in which we added some of our final project's GitHub issues as sample data.
