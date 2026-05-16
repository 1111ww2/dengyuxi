---
title: Deployment and Integration – Implementation, Quality and Maintenance
date: 2026-05-09
author: Yuxi Deng
summary: How our group connected routes, controllers, SQLite, HTMX, and deployment considerations to turn Sydney Life Aid into a working web app prototype.
tags:
  - blog-5
  - Workflows
  - APIs discussion
  - Hosting and maintaining 
---
### Part 1: From Development to a Working Prototype

Week 10 helped me understand that a web app should not only stay as a local page design. It also needs to consider development, deployment, maintenance, and integration. In Sydney Life Aid, we connected the page structure, user flow, routes, controllers, SQLite database, and partial views into a working prototype. When users search, publish, save, like, or comment, the action goes through a route and controller, reads or updates the database, and then returns a page or partial update.

### Part 2: Database Reading, User Actions, and System Responses

![](assets/images/5.1.png)

Our technical choices were based on user tasks, not on showing technology for its own sake. Read-only functions use GET and SQLite queries. For example, `/task` reads tasks, `/community` reads peer experiences through search and task filters, and `/address` reads places. Write-based interactions use POST, such as `/release` for publishing, `/save-place/:id` for saving places, and like or comment routes for updating interaction data.

HTMX is used for small interactions such as saving, liking, commenting, and replying. After a user action, only the related button, like count, or comment area updates, instead of refreshing the whole page. This makes the platform feel more like a real web application.

### Part 3: Deployment, Integration, and Future Extension

![](assets/images/5.2.png)

Deployment needs to match the project type. A static website such as the A1/A3 blog can be published through GitHub Pages and GitHub Actions. However, Sydney Life Aid includes backend routes, SQLite, sessions, and user interactions. If it were published in the future, it would need a hosting environment that supports backend execution, rather than only GitHub Pages.

For integration, we did not include a real Map API in the MVP. Instead, we used place cards and external Google Maps links. This still helps users find GP, pharmacy, and emergency care, while avoiding extra complexity from API keys, quotas, costs, and error handling. Map API, translation API, or recommendation systems can remain as future scope.

### Part 4: Safety, Maintenance, and Implementation Adjustments

![](assets/images/5.3.png)

During implementation, we found that pages, routes, database fields, and partial views must stay consistent. Otherwise, pages may display correctly, but search, filtering, saving, or partial updates can fail. Therefore, we unified route names, field names, component structure, and CSS classes.

The MVP only keeps necessary data for login, publishing, saving, liking, and commenting. It does not collect real names, insurance numbers, or detailed medical records. User input needs validation and safe rendering, and database queries need parameterised queries to reduce SQL injection risks. For repeated actions such as saving a place or liking a post, we used `INSERT OR IGNORE` to avoid duplicate records.

### Design Decisions

1. We connected technical choices to user tasks. GET reads tasks, places, and posts; POST handles publishing, saving, liking, and commenting; HTMX supports partial updates.

2. We controlled the MVP deployment and integration scope. Instead of adding Map API, real-time chat, or recommendations, we used SQLite, routes, controllers, templates, and Google Maps links to complete the core pathway.

### Personal Reflection

Implementing a web app is not only about making the code run. It also requires thinking about deployment, maintenance, safety, and future extension. At first, I thought completing pages and database tables would be enough. However, I realised that if routes, controllers, database fields, or partial views are inconsistent, the function can fail. Technical choices should support user tasks, not make the project look complex. For our project, stable browsing, place finding, reading experiences, publishing, and interaction are more important than adding advanced features too early.

These decisions were discussed and finalised together. All diagrams and code implementation were created collaboratively.