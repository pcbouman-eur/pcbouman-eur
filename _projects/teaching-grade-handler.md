---
layout: page
title: Grade Handler
description: Browser based grade handling
img: assets/img/teaching_grade-handler.jpg
importance: 1
category: teaching
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/teaching_grade-handler.jpg" title="Source: Photo by Andy Barbour from Pexels" alt="A teacher writing an A+ on an exam paper" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project aim to make combining and preparing grade lists easier for teachers at **Erasmus School of Economics**,
so error-prone `VLOOKUP`/`INDEX/MATCH` types of operations can be avoided, while providing a number of quality-of-life
sanity checks out of the box.

**Note:** this tool is **not** meant as a general purpose grade handler for teachers at other universities,
as it makes a hard assumption that student identifiers have the format used at Erasmus University Rotterdam.
This assumption allows for a smoother user experience, as identifying columns can be detected automatically.
However, the tool is open source so ideas can be taken/adopted by others if desired.

A [live version](https://pcbouman-eur.github.io/ese-grade-handler/) of the tool can be found on Github, as well as the [source code](https://github.com/pcbouman-eur/ese-grade-handler).
The tool was build as a handy prototype, with the (likely very naive) aim of motivating our school and/or university to make a more professional version of this tool.

## Background

Over the course of my teaching at ESE, I had developed a number of scripts that allowed me to combine spreadsheets of exams (either manually created or exported by examination software),
and the grades of assignments as exported by our Learning Management System (Canvas). Since command line scripts are not the most user friendly things to share, whereas more and more
fantastic libraries became available to do all kinds of things traditionally reserved for desktop applications purely client-side on the web browser, I started experimenting to see
if the job done by my scripts could be done in a client-side web application.

It turns out that this is quite possible. The free version of the [SheetJS](https://sheetjs.com/) library can be used to extract relevant data out of all kinds of spreadsheets,
and also to generate new spreadsheets that can be downloaded by the user. The really nice thing is that no data needs to be transmitted to a server to handle the spreadsheet server side,
but that all reading and writing of spreadsheets can happen inside the browser. However, the free version does come with it's limitations and is not as powerful as the most popular
Java or Python libraries for handling spreadsheet files.

I currently use the Pandas inspired [Danfojs](https://github.com/javascriptdata/danfojs) to create data frames out the spreadsheet data (although in hindsight I am not sure if this is needed).
In an ideal version of this tool, I could imagine having a proper database per course. But for now, this works.

The UI is designed using the excellent [Vue Framework](https://vuejs.org/) with the [Vuetify Component Framework](https://vuetifyjs.com/).
This allows me to create nice looking, reactive user interfaces without too much hassle. What I particularly like about Vue is that you
can start using it for a small part of a normal HTML page, and slowly progress towards more advanced use in a project for a single page 
application (which I built here).

Finally, our grade administration introduced a rule that grade changes should be performed with individual word documents per grade change (resulting in a lot of outrage among teachers).
In an attempt to smoothen out this bureaucratic nightmare, I added a feature that uses [docx javascript library](https://docx.js.org/)
together with the [jszip library](https://github.com/Stuk/jszip) that generates a `.zip` file containing a word document with a filled-in form for each row in the input spreadsheet,
again all within the confines of the user's browser. The signature of the user can be drawn using the [vue-signature component](https://github.com/WangShayne/vue-signature) and is
injected into the generated word files.

