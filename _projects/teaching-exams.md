---
layout: project
title: Examination Software
description: Performing remote examination for IT-related courses
img: assets/img/teaching_exams.jpg
img_title: Photo by RODNAE Productions on Pexels
img_alt: A teacher supervising students during an exam
importance: 2
category: teaching
---

In this project I developed educational software to facilitate online proctored examination of IT-related courses involving programming tools or other software. The particular focus was to be able to provide customized question types to students that typically are not facilitated by regulator examination software. During this project I received a lot of valuable advice from Pleuni de Kock, whose background in educational science and professional experience with digital exams proved crucial in getting the details right needed to provide a smooth experience to the learners.

## Background

During the COVID-19 pandemic, the Dutch government imposed severe restrictions on society that also impacted examinations at
universities. Erasmus University decided to apply online proctoring to deal with this situation. However, this posed a challenge for
examination of courses where programming education or tools such as Microsoft Excel were needed by students, as the secure environment
Erasmus University developed for these examinations could not be accessed by students via the internet. This raised the question how we 
could provide a uniform and consistent examination environment for students in these courses.

With the many capabilities offered by the modern and the fact that students had to use a modern webbrowser to make their exams, the
idea rose to exploit the flexibility offered by the modern web to provide tailor made learning and examination experiences to the
students. I developed a frontend using [Vue.js](https://vuejs.org/) and [Vuetify](https://vuetifyjs.com/) that made it very easy to
develop custom question types, for example based on the [Monaco Editor](https://microsoft.github.io/monaco-editor/) developed by
Microsoft that also powers Visual Studio Code, or the [Blockly Library](https://developers.google.com/blockly) developed by Google that
provides a visual programming editor in the browser. As each question consists of a JSON-data with a `type` attribute indicating which
UI-component should be used to let the student interact with the question, there is a lot of flexibility to design and develop novel
types of questions that are not offered out-of-the-box in standardized educational tools, such as the
[Canvas LMS](https://www.instructure.com/canvas) or the [Ans examination software](https://www.ans.app).

During the pandemic, this tool was used for a number of exams. The tool was served from a backend I developed on top of [Spring Boot](https://spring.io/) with authentication via an LTI-integration with Canvas.

## Future: External Questions 

Currently I am exploring the possibility to serve parts of the frontend developed during the pandemic without the need of maintaining and operating a backend. The idea is to include all relevant data inside links so that the new question types can be shared from traditional educational tools such as Canvas or Ans without additional depedencies. I have adapted certain question types in this alternative setup in a public Github repository.
There is a [live demonstration](https://econometricinstitute.github.io/external-question/) of this external questions setup of the tool. The [source code](https://github.com/EconometricInstitute/external-question) is also visible.

