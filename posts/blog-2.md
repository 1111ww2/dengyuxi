---
title: Process – Functions and Architecture
date: 2026-04-18
author: Yuxi Deng
summary: How our group shifted from a website mindset to a task-oriented web app, defined the core user flow, prioritised MVP features, and designed the page structure and interactions.
tags:
  - blog-2
  - User flow diagrams
  - Sitemaps
  - Wireframes
---
### Part 1: From Website to Web App

Week 7 helped me re-understand the difference between a website and a web app. Before, I focused on “what content should be shown on the page”. However, Week 7 emphasised that a web app should be designed around user tasks, behaviours, and system responses, not only information navigation. Therefore, our project should not just display medical information, but help users complete “seeing a doctor in Sydney”. We shifted from “what is on the page” to “what users need to complete” and “how the system supports them”.

### Part 2: User Tasks, Needs, and Feature Prioritisation

![](assets/images/2.1.png)

Our target users are Chinese international students in Sydney. When they feel unwell, injured, or unsure whether they need to see a doctor, they need to quickly judge what to do next. Therefore, we summarised the core task as: judge the situation — choose a task — read experiences — find a place — save information — participate in the community.

Based on this path, we analysed what functions users need and separated MVP core features from secondary features. The MVP core features include task entry and browsing, task detail pages, a step-by-step task path, related place cards, peer experience cards, and basic save place and question / feedback functions. These directly support the core doctor-seeking path. Map API, real-time chat, notifications, and user levels are valuable, but not minimum requirements, so we placed them in future scope to avoid MVP scope creep.

### Part 3: Overall Website Page Structure

![](assets/images/2.2.png)

To support the core functions, we built the page structure from the user task path. The Home / Task Page is the core entry point for browsing medical tasks. The Community Page supports reading and searching peer experiences. The Post Detail Page shows full posts and interactions. The Release Page supports publishing questions or experiences. The Address Page helps users find GP, pharmacy, or emergency locations. The Settings Page manages personal information, saved places, and interaction records.

### Part 4: Website Flow and User Action Responses

![](assets/images/2.3.png)

The Web Flow Diagram shows the complete flow from entry point to action. The wireframe flow explains how user actions trigger system responses. For example, after users click a task card, the system enters the related Community Page and filters posts. After searching or filtering, the post list updates. After clicking a post, users enter the Post Detail Page. After clicking save place, the place is saved to the personal page. After submitting a question, a new question card is generated.

### Design Decisions

1. We summarised the core user task into a complete action path and separated MVP core features from secondary features.

2. We built the website page structure around the core task. Each page responds to a clear user need, and the flow diagrams clarify system responses such as task filtering, search updates, saving places, and generating question cards.

### Personal Reflection

At first, I still understood the website through page numbers and navigation structure, but Week 7 made me realise that a web app is more about user tasks and system responses. We originally wanted map API, real-time chat, notifications, and user levels, but later found these features would make the MVP more complex. This trade-off helped me understand that a good web app is not about more features, but about making sure every page and interaction supports users in completing the core task.

These decisions were discussed and finalised together. Liuyufei was responsible for Figure 1, I was responsible for Figure 2, and Figure 3 was created together.