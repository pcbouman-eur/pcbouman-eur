---
layout: project
title: Scheduling of TA's
description: Assigning classes to teaching assistants
img: assets/img/teaching_taschedule.jpg
img_title: Photo by cottonbro studio on Pexels
img_alt: A whiteboard with a activities, months and post-its indicating who will do what
importance: 2
category: teaching
---

In this project I developed educational software to support me in assigning teaching assistants to classes they have to teach. 

In my second year programming course in our Econometrics programs I typically have around eight student assistants to schedule.
In my first year Introduction to Data-analytics course I typically have between twenty and thiryt student assistants to schedule.
Finding a nice schedule that fits the preferences and availability of all student assistants, while ensuring that students have
the same teacher for their different classes is a challenging puzzle.

## Scheduling Problem

Due to my background in computer science and operations research, it is obvious to think about
this scheduling problem in terms of mathematical optimization.

Assume we have a set of bundles of teaching tasks $B$ and for each of those bundles $b_i \in B$ 
we have a minimal number $b_i$ of teaching assistants we want to assign to that bundle of tasks.
Furthermore, we have a set of teaching assistants $T$ and for each teaching assistant $t \in T$,
we then have a set $S_t$ of feasible schedules we can assign to that teaching assistant. For each
schedule $s \in S_t$ and each bundle of tasks $b_i \in B$
we have an indicator variable $a_{s,i}$ which is $1$ is schedule $s$ contains task bundle $i$,
and $0$ otherwise. Finally, for each schedule $s \in S_t$ we have a *preference score* $p_{t,s}$
indicating how attractive that particular schedule is.

Putting all these variables together, allows us to write the scheduling problem using the
following *schedule-oriented* formulation:

$$
\begin{alignat}{2}
      \max & \sum_{t \in T} \sum_{s \in S_t} p_{t,s} x_{t,s} & & \\
\text{s.t} & \sum_{s \in S_t} x_{t,s} & = 1 & \forall t \in T \\
           & \sum_{t \in T} \sum_{s \in S_t} a_{s,i} x_{t,s} & \geq b_i & \forall i \in B \\
           & x_{s,t} & \in \{0,1\} & \forall t \in T, \forall s \in S_t   
\end{alignat}
$$

There are some challenges when working with this formulation. First, the question is how to combine
teaching tasks into bundles. Second, the number of feasible schedules for a particular TA can be gigantic
if they are very flexible. Finally, we need to come up with a way in which to compute the *preference score*.

A different formulation could be defined using decision variables that directly assign bundles to
student assistants, rather than choosing one schedule per student assistant. We call this alternative formulation
the *bundle oriented* formulation.

### Defining bundles of Teaching Tasks

As the teaching tasks of my largest courses can approach 500 tasks, defining bundles by hand is too
cumbersome. I developed an algorithm that groups teaching tasks according to the *student group*
and the *time of the activity in the week*. This generates for examples bundles that contain all
tutorials for group EC01 from 9:00 - 11:00 on Tuesdays. Another bundle could be all tutorials for
group EC02 from 13:00-15:00 on Thursdays.

As some manual modification of a schedule is typically needed, the bundles of teaching tasks are
assigned intuitive names, derived from the student groups. In the example above, we would have a
bundle with name EC01-a and a bundle with name EC01-b. If for example all teaching activities of
group EC02 would occur at the same time within each week, no suffix would be applied and the
bundle is just called EC02.

### Determining Individual Schedules

In practice I have had cases where some student assistants had only a handful of feasible schedules
whereas others had millions. To determine whether a schedule is feasible, the following hard constraints
are considered:

* The maximum total workload of the student assistant can not be violated
* The maximum weekly workload of the student assistant can not be violated
* No combinations of bundles that contain overlapping teaching activities can be within the same schedule
* No bundles that contain teaching activities at a time the student assistant is unavailable can be in their schedule
* The capabilities of the student assistant match those required for all teaching activities in the bundle (e.g. language related capabilities)

Note that all these constraints can be easily taken into account in both the *schedule oriented* and the *bundle oriented*
formulations. However, things become more complicated when we consider some soft constraints that we aim to take into
account in the *preference score*.

### Determining the preference scores

We try to capture are number of factors in the *preference score*, some of which are preference from the side
of the student assistant, while others are preferences for the students. The factors I currently consider are
the following:

* The preferences of the student assistant for the time slots where they are available (on a 5-step scale)
* The preferences of the student assistant for particular types of student groups (e.g. fiscal economics vs regular economics)
* The preferences of the student assistant to perform different numbers of consecutive teaching tasks
* The preferences of the student assistant to perform teaching activities on different numbers of days within each week
* The number of times the student assistant teaches the exact same group of students

As some of these preferences depend on exactly which bundles are selected together, including all these in the preference
scores is significantly harder in the *bundle oriented* formulation.

## Software

I have created multiple iterations of software for this scheduling process. I hope some day the latest iteration of this
software will at some point be flexible and user friendly enough to use by colleagues. Currently, I have a tool that
can convert a spreadsheet exported from our time tabling software to a scheduling instance. It can then use that instance
to create a preferences survey to be filled in by the student assistants. Using the data from these surveys, a schedule
can be made by dragging and dropping task bundles in a table format, where the total preference scores as well as the
violations of constraints are immediately indicated by the software. There is also an option to run a few steps of
a greedy heurstics. Hopefully, smarted approaches can be added to the software in the future.

The repository of this software is on [Github](https://github.com/pcbouman-eur/ta-scheduling), but unfortunately it is
not documented yet.