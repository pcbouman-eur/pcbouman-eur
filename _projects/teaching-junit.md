---
layout: project
title: Student testing tools
description: Better automated feedback for students using JUnit5 plugins
img: assets/img/teaching_cgjunit5.png
img_alt: The logos of Codegrade and JUnit 5
importance: 1
category: teaching
---

This project is about educational software development. The code can be found on [github](https://github.com/pcbouman-eur/student-test-tools).

For my teaching in the course FEB22012X Programming, I rely heavily on the
[Codegrade](https://www.codegrade.com/) application to provide automated
feedback to students. The main advantage of this is that students can
keep working on their assignment and fix their mistakes. This way, students
can learn from practice by fixing their mistakes, rather than getting one
shot feedback at the end of their assignment work.

This requires that the teacher writes software that can check and provide
feedback for the student's code. Working with Java, it makes sense to
make use of the popular tooling that was developed for testing Java programs,
of which JUnit is a very popular option. However, there are a couple of drawbacks
working with plain JUnit:

* Assertions that pass successfully are discarded by standard unit testing frameworks. When providing feedback to students, it is valuable and encouraging to provide feedback on things that are correct.
* Standard runners for JUnit tests may result in very long stacktraces of which only a small part is relevant. It can be helpful for students to only show the interesting part.
* Standard unit tests stop as soon as an assertion fails - this makes sense as their main purpose is to warn developers something broke. However, for student it may be useful to communicate if more issues can be found with their code. Splitting each assertion up over a separate test method is not always convenient.
* There is no natural support to define that at least some but not necessarily all test cases should pass. If we want to allow students to choose between different parts of the assignment, this is typically needed.
* Missing methods or mistakes in student code may result in *missing symbol* errors when compiling the test code. As a consequence, students will see compiler errors in code written by the teacher. Some will thus assume the mistake is at the side of the teacher, and not at the side of the student.

In this project, I have developed some tools that can address these issues. Details on how this is achieved are discussed on [the github page](https://github.com/pcbouman-eur/student-test-tools).
