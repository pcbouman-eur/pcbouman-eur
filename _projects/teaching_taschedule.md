---
layout: project
title: Scheduling of TA's
description: Assigning classes to teaching assistants
img: assets/img/teaching_taschedule.png
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

Putting all these variables together, allows us to write the scheduling problem as follows:

$$
\begin{alignat}{2}
      \max & \sum_{t \in T} \sum_{s \in S_t} p_{t,s} x_{t,s} & & \\
\text{s.t} & \sum_{s \in S_t} x_{t,s} & = 1 & \forall t \in T \\
           & \sum_{t \in T} \sum_{s \in S_t} a_{s,i} x_{t,s} & \geq b_i & \forall i \in B \\
           & x_{s,t} & \in \{0,1\} & \forall t \in T, \forall s \in S_t   
\end{align}
$$

