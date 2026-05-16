---
title: Modular Design – Layout and Components
date: 2026-04-26
author: Yuxi Deng
summary: How our group used modular design to organise Sydney Life Aid with a shared layout, reusable components, partial views, and clearer teamwork.
tags:
  - blog-3
  - Design system
  - Reusable components
  - Modular code structure
---
### Part 1: Modular Design

Week 8 helped me understand that a web app needs modular design because many pages repeat similar content and interactions. If every page is designed and coded separately, it wastes time and can create UI inconsistency. Therefore, we organised Sydney Life Aid with a shared layout, partial views, and reusable components to reduce repeated code, support teamwork, and support maintenance.

### Part 2: Layout and Wireframes

![](assets/images/3.1.png)

Following Week 8’s modular design idea, we divided the page structure into layout and partial views. The layout is the shared skeleton of the website, while partial views are reusable components that can be inserted into different pages and support HTMX partial updates.

We created wireframes to show the main pages and user task path. Users enter through Login / Create User, browse medical tasks on the Home / Task Page, read peer experiences on the Community Page, find GP, pharmacy, or emergency locations on the Address Page, publish questions or experiences on the Release Page, and manage saved places and records on the Settings Page. The website is built around the task of “finding medical help”.

### Part 3: Trade-offs and Components

![](assets/images/3.2.png)

After deciding the page structure, we reflected on the trade-offs of modular design. Shared navigation, reusable cards, shared CSS, and database relationships improve consistency. However, modularity also has limits. A unified navigation may weaken the main task path, different cards need different data fields, and HTMX partial updates depend on stable controller data. Therefore, we needed consistent database fields, component names, and CSS classes.

We transformed user needs into reusable components, including Header / Navigation, Task Card, Experience Card, Place Card, Save Place Button, and Profile Activity Cards. Each component supports a clear user behaviour, such as browsing tasks, reading experiences, finding places, saving information, or joining community interaction.

### Part 4: Teamwork and Implementation

![](assets/images/3.3.png)

We divided the work by the user journey rather than randomly splitting pages. Yufei worked on the Task Flow / Preparation Module, focusing on task entry, pathways, and preparation steps. I worked on the Place / Community / Experience Module, focusing on places, peer experiences, questions, publishing, and saving functions. We also unified component naming, CSS, page style, and data fields so the site worked as one web application.

In the code, the `partials/` folder stores reusable components. `views/layouts/default.html.tmpl` is the shared layout, including Header / Navigation, language switch, user entry, Main Content Area, and Footer. Different page content is inserted into this shared structure.

### Design Decisions

1. We used modular design to organise the website with a shared layout, page templates, and partial views, while unifying component naming, CSS, and page style.

2. We defined the structure around the user task path: user task path → page structure → repeated components → layout / partial views → routes / controller / database.

### Personal Reflection

I clearly felt the importance of modular design for group collaboration. At first, we only wanted to build pages, but after writing code, we realised that without shared layout, naming, and CSS rules, two people could easily create pages with different styles and structures. Modular design also made it easier to find the right code when changing things. This helped me understand that a good web app needs not only visual design, but also a clear, maintainable, and expandable structure.

These decisions were discussed and finalised together. Liuyufei was responsible for Figure 1, and I was responsible for Figure 2.