---
layout: project
title: Spread out to school
description: Smart division of school groups over timeslots
img: assets/img/impact_spreadschool.jpg
img_alt: A school child wearing a face mask
img_title: "Source: Photo by Max Fischer from Pexels"
importance: 1
category: impact
---

This project is joint work with [Twan Dollevoet](https://www.erim.eur.nl/people/twan-dollevoet/),
[Remy Spliet](https://www.erim.eur.nl/people/remy-spliet/)
and [Wilco van den Heuvel](https://www.erim.eur.nl/people/wilco-van-den-heuvel/)
 and was a nice project where we provided a tool to assist grade school replanning their classes
 during the COVID-19 pandemic.

During the COVID-19 pandemic, some grade schools decided to split student groups in half in order
to reduce contact between children. Physical school attendance would then alternate over the
days for the two halfs, meaning that every day one half of the children in each groups would
have to be home schooled. The aim of the tool is to make the division in a smart way, such
that as much as possible all children of the same family would go to school on the same day.

Underneath our approach was a simple optimization model:
given a set of $$n$$ (already splitted) groups $$C = \{1, \dots, n\}$$,
an overlap matrix $$A \in \mathbb{Z}^{n \times n}$$ and a number of timeslots $$k$$ (typically 2),
the goal is to partition $$C$$ into $$k$$ sets $$P_1, \dots, P_k$$ of cardinality between
$$\lfloor \frac{n}{k} \rfloor$$ and $$\lceil \frac{n}{k} \rceil$$,
maximizing the sum of the overlaps within each partition,
i.e. $$\sum_{s=1}^{k} \sum_{i \in P_s} \sum_{j \in P_s : i < j} A_{ij}$$.
The idea is that the overlap coefficients indicate that a pair of groups have children from the same
family, and that ideally these groups should come to school in the same timeslot.

We provided a fully client side web-based application (in Dutch) where teachers could enter
the number of groups, the overlap matrix and the number of timeslots. We then use both
a heuristic to quickly obtain a good solution, and a full enumeration algorithm to obtain
the best solution. These algorithms are executed fully inside the web-browser,
making it possible for schools to use our optimization techniques without having to
install any software, and without requiring them to share any data.

The tool itself can be [accessed via Github Pages](https://econometricinstitute.github.io/VerspreidNaarSchool/)
(the tool is in Dutch). The [source code](https://github.com/EconometricInstitute/VerspreidNaarSchool)
is also available under an MIT License. 

## Societal Impact

Our tool was featured in different outlets:

* A [news article](https://www.eur.nl/en/news/spread-out-school-tool-helps-primary-schools-and-parents-corona-proof-lesson-scheme) on the main site of Erasmus University Rotterdam
* A [news article in Dutch Newspaper Algemeen Dagblad](https://www.ad.nl/rotterdam/praktisch-en-coronaproof-lesrooster-met-slimmigheidje-rotterdamse-econometristen~a60ac96e/), the second largest nationwide newspaper in the Netherlands
* A [news article on Dutch News Site nu.nl](https://www.nu.nl/rotterdam/6116500/coronaproof-rooster-op-scholen-rotterdam-door-hulp-econometristen.html), a popular free Dutch news site.