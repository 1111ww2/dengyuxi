---
title: Database Implementation – DDD and ERD
date: 2026-05-04
author: Yuxi Deng
summary: How our group worked backwards from wireframes and user flow to design the DDD, ERD, and SQLite database structure for the Medical Help Task Platform.
tags:
  - blog-4
  - Data structures
  - DDDs
  - ERDs 
---
### Part 1: Working Backwards from Interface to Data

Week 9 helped me understand that database design should not start directly from code. Instead, it should be worked backwards from wireframes and user flows. Database design needs to support user actions, page changes, and functional implementation.

### Part 2: Identifying Data, First DDD and ERD

![](assets/images/4.1.png)

We identified three types of data from the wireframes and user flow: displayed data, input data, and generated data. Displayed data is shown on the page, input data comes from user actions, and generated data is created or updated by the system. Based on this, we organised nine possible data objects.

Through listing, analysis, and discussion, we selected Task, TaskStep, Place, and PeerExperience as the core data objects. We then used an ERD to clarify the core database structure. The platform mainly supports the “See a doctor in Sydney” pathway through task flow, place selection, and peer experiences.

### Part 3: Consultation and Iteration

![](assets/images/4.2.png)

After completing the first DDD and ERD, we found that although the original ERD kept the four core entities, the relationships were still quite conceptual. It was closer to listing the main content than showing real website behaviours such as login, questions, saving places, comments, and likes. Therefore, we asked a CS student to conduct a technical feasibility review.

The feedback helped us realise that if all objects from the first DDD were implemented as dynamic database tables, it would increase the complexity of models, SQL queries, controller handling, and template rendering. However, if we only kept the four core entities, the website would not fully support community interaction.

### Part 4: Final DDD and ERD

![](assets/images/4.3.png)

After the technical feasibility review, we divided the data into core queryable data and supporting / simplified data. The core entities are Task, TaskStep, Place, and PeerExperience. They support task selection, step guidance, place finding, and experience reading. The supporting entities are User, Question, SavedPlace, ExperienceComment, and ExperienceLike. They support login, asking questions, saving places, commenting, replying, and liking. This made the database structure more practical while still supporting the main user pathway.

### Part 5: Database, Pages, and Implementation

![](assets/images/4.4.png)

Sydney Life Aid has moved from page design into a working web app implementation. The main content is not hard-coded in HTML. Instead, tasks, places, posts, users, saved places, comments, and likes are stored and read through SQLite.

`src/models/medical.ts` implements the DDD and ERD as database tables. `src/controllers/medical.ts` gets tasks, experiences, comments, and saved data from the model, then passes them to the view. Finally, `medical/experiences.html.tmpl` uses a template loop and the `experience-tile` partial to render peer experiences as community post cards.

### Design Decisions

1. We worked backwards from wireframes and user flow to database design. We first identified what data needed to be stored and read, then kept Task, TaskStep, Place, and PeerExperience to support the core pathway.

2. We adjusted the data scope through the technical feasibility review and added supporting entities to connect real page functions. The final structure follows the logic of database → model → controller → template → page, turning the site from static pages into a working web application.

### Personal Reflection

Database design felt more like a design problem than just a technical problem. At first, I thought every piece of page content could become a data table. However, the technical feasibility review reminded us that data structures should support user behaviour, not exist only for completeness. If everything became dynamic, the MVP would become too complex. By separating core data from supporting data, I learned that good database design is not about having more tables, but about improving the core functions.

These decisions were discussed and finalised together. All diagrams and code implementation were created collaboratively.The iteration from Figure 1 to Figure 3 referenced the user's technical feasibility review.