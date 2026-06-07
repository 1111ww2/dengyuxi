---
title: Reflection-From Running Correctly to Truly Supporting User Action
date: 2026-06-07
author: Yuxi Deng
summary: A final reflection on Sydney Life Aid, focusing on performance, user experience, functional requirements, testing limits, and future improvements.
tags:
  - blog-7
  - Final reflection
  - Performance
  - User experience
  - Future improvements
---
Sydney Life Aid is a help platform for Chinese international students in Sydney who need support with seeing a doctor. It is built around “See a doctor in Sydney” as a task-oriented community hub. Instead of treating healthcare information as a list of links, the project turns a vague and fragmented real-life problem into an action process that can be understood, searched, supported by peer experiences, and extended by the community. The key question is no longer only whether the website can run, but whether it can help a user move from uncertainty to action.

### Performance

From a technical perspective, the basic operation of Sydney Life Aid is stable. We used Mojo.js, TypeScript, SQLite, HTMX, and an MVC structure to separate page presentation, route control, database models, and partial interactions. According to the testing records, the project can complete `npm install`, `npm run seed`, and `npm run dev`, and it can open locally without obvious 404, 500, or routing errors. TypeScript check, lint check, model test, and route test also prove that the core code structure has reliability. Database-related tests show that posts, comments, replies, likes, saved places, and permissions are not only page displays, but can be persistently stored through SQLite.

This process helped me understand the meaning of “mechanical correctness” discussed in the later course weeks. Testing is not used to prove that the work is perfect, but to locate the conditions under which the system still runs correctly. When a comment is submitted, the interaction depends on the route, controller, model query, database relationship, template partial, and HTMX target working together. This made me realise that a full-stack prototype requires both interface thinking and system thinking.

However, this stability also has clear boundaries. The prototype was mainly verified locally, not in a real deployment environment with different networks, devices, browsers, and user scale. Therefore, I cannot simply claim that the system has “good performance”. A more accurate conclusion is that it is stable within the course prototype scope. HTMX improved interactions such as like, comment, save, and unsave, but it increased debugging complexity because errors may come from templates, controllers, model queries, targets, or partial responses. Future evaluation should include deployed testing, mobile network testing, browser checks, and more systematic performance evidence.

![](assets/images/7.1.png)

### User Experience

The biggest strength of Sydney Life Aid is that it organises content around user tasks. The Home page uses a task pathway to help users understand the general steps of seeing a doctor. The Address page presents GP, pharmacy, emergency, and student support locations in one place. The Community page allows users to read peer experiences. The Release page allows users to publish their own questions or experiences. The Settings page stores users’ personal information, posts, liked content, and saved places. The user testing scenario was a Chinese international student in Sydney feeling unwell and needing to know how to see a doctor, where to go, and what to prepare. This matches the target users and is more valuable than simply checking whether buttons can be clicked.

Testing results show that users can understand the basic purpose of the platform and complete core tasks such as browsing the flow, finding places, reading experiences, saving places, and simulating publishing. This supports the direction proposed in the Dev Blog stage: helping Chinese international students reduce anxiety around the medical process. The Chinese-English switch is also an important design decision because the target users may not fully understand English terminology in the Australian healthcare system. Through a bilingual interface, the platform becomes more inclusive in terms of information understanding and better fits the real situation of the target community.

At the same time, user experience testing revealed important weaknesses. The login page did not communicate the website theme strongly enough at the beginning. This means the entry point had weak information scent. Before entering the system, users should quickly understand that this is an action-support platform about seeing a doctor in Sydney, not a normal account page. On the surface, this is a visual and copywriting issue; more fundamentally, it is an information architecture issue. If users cannot build the right expectation at the entry point, the value of later functions will be weakened. Accessibility was also considered through responsive layout, form hints, consistent buttons, contrast, and readability, but it still remained at a basic checking level. Following the course discussion of WCAG AA and inclusive design, “being usable” should only be the minimum standard. A better design should support different language abilities, technical familiarity, anxiety levels, and accessibility needs.

![](assets/images/7.2.png)

### Evidence and process

<style>
/* Blog 7: force the testing-summary pages to stay in one horizontal swipe row after publishing */
.pdf-slider {
  width: 100%;
  max-width: 100%;
  margin: 2rem 0;
  padding: 1rem;
  border: 1px solid var(--border);
  border-radius: 24px;
  background: rgba(255, 253, 251, 0.9);
  box-shadow: var(--shadow-card);
  overflow: hidden;
}

.pdf-scroll {
  display: flex !important;
  flex-direction: row !important;
  flex-wrap: nowrap !important;
  gap: 1rem;
  width: 100%;
  max-width: 100%;
  overflow-x: auto !important;
  overflow-y: hidden;
  scroll-snap-type: x mandatory;
  -webkit-overflow-scrolling: touch;
  padding: 0.25rem 0 1rem;
}

.pdf-scroll img {
  display: block !important;
  flex: 0 0 92% !important;
  width: 92% !important;
  min-width: 92% !important;
  max-width: 92% !important;
  height: auto !important;
  margin: 0 !important;
  scroll-snap-align: center;
  border: 1px solid var(--border);
  border-radius: 18px;
  background: var(--surface);
  box-shadow: var(--shadow-card);
}

@media (min-width: 900px) {
  .pdf-scroll img {
    flex-basis: 82% !important;
    width: 82% !important;
    min-width: 82% !important;
    max-width: 82% !important;
  }
}
</style>

<div class="pdf-slider" aria-label="Testing summary image gallery">
  <div class="pdf-scroll">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_01.png" alt="Testing Summary page 01">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_02.png" alt="Testing Summary page 02">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_03.png" alt="Testing Summary page 03">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_04.png" alt="Testing Summary page 04">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_05.png" alt="Testing Summary page 05">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_06.png" alt="Testing Summary page 06">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_07.png" alt="Testing Summary page 07">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_08.png" alt="Testing Summary page 08">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_09.png" alt="Testing Summary page 09">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_10.png" alt="Testing Summary page 10">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_11.png" alt="Testing Summary page 11">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_12.png" alt="Testing Summary page 12">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_13.png" alt="Testing Summary page 13">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_14.png" alt="Testing Summary page 14">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_15.png" alt="Testing Summary page 15">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_16.png" alt="Testing Summary page 16">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_17.png" alt="Testing Summary page 17">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_18.png" alt="Testing Summary page 18">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_19.png" alt="Testing Summary page 19">
    <img src="assets/images/blog-7-pdf/Testing%20Summary%20Final%20%282%29_20.png" alt="Testing Summary page 20">
  </div>
</div>


### Functional Requirements

I think the most successful part of the project was controlling the scope in time. The final MVP kept the most important user paths: understanding the process, finding places, reading experiences, publishing content, and managing personal information. This reduction was necessary. If we continued to expand functions, the project could easily become a messy information platform and lose the core value of being task-oriented. For this topic, the website should not answer every healthcare question. It should help users make the next appropriate decision: go to a pharmacy, book a GP, prepare OSHC information, read a peer experience, or seek emergency support.

The AI Statement also records that we used AI to analyse page structure and judge which functions should be kept, merged, or removed (The AI Statement also records that we used AI to analyse page structure and judge which functions should be kept, merged, or removed ([AI Statement](https://drive.google.com/file/d/1ltcNttOS24i8r1Vs5I15XodBI5PUE8X2/view)), but the final design judgement still came from our understanding of the target users and project scope.), but the final design judgement still came from our understanding of the target users and project scope. AI helped organise options, identify inconsistencies, and support debugging, but it did not replace design judgement. The final MVP still had to be shaped by the brief, user needs, time limits, technical feasibility, and ethical responsibility.

At the same time, I realised that the original functional requirements still had incomplete aspects. First, medical information is high-risk. The platform should not rely only on user-generated content. It needs source dates, official links, review mechanisms, and clearer emergency disclaimers. Second, the task pathway currently works more like guidance than an adaptive decision system. Future versions could ask simple questions and direct users to relevant steps or services. Third, the fact that only three Chinese students were invited to participate in the test may have limitations in sample size.

![](assets/images/7.3.png)

If I continue development, I would prioritise three types of improvements. First, I would strengthen onboarding by adding a clearer explanation of the platform, target users, and emergency boundaries on the login and Home pages. Second, I would build a more reliable data and content mechanism by adding updated dates for places, review labels for posts, and explicit “peer experience, not professional advice” messages. Third, I would conduct more systematic performance and accessibility evaluation, including Lighthouse, keyboard-only testing, screen reader checks, mobile loading tests, and deployed API fallback testing.

![](assets/images/7.4.png)

### Lessons Learned

Web development is not simply about making an interface. It is about turning a complex problem into an action pathway that can be supported by a system. A1 Dev Blog helped me learn how to define the problem through research and concept development. A2 Web App Prototype helped me turn the problem into routes, templates, database relationships, and interactive behaviours. A3 Reflection helped me judge whether the prototype was truly effective, where the evidence was strong, and where the conclusion should be more cautious.

The biggest lesson is that design quality does not only come from adding more features. It comes from matching the system structure with the user’s problem. For Chinese international students who are unfamiliar with the local healthcare system, what is truly helpful is not more scattered information, but clear steps, trustworthy places, peer experiences that can be referenced, and a structured platform that helps them move from anxiety to action. Sydney Life Aid is still only a course-scope prototype, but it has already proved a meaningful direction. If it were developed further, the next challenge would be to make it not only functional and understandable, but also safer, more accessible, more evidence-based, and more trustworthy in a real-world context.
