---
layout: page
title:  TSP with Drone
description: Routing of a paired truck and drone
img: assets/img/research_tdp-d.png
importance: 1
category: research
---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/research_tdp-d.png" alt="A diagram when a truck drives from the depot to four nodes, and a drone flies from the truck to two other nodes" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This project is joint work with [Niels Agatz](https://www.rsm.nl/people/niels-agatz/) and
[Marie Schmidt](https://www.informatik.uni-wuerzburg.de/en/algo/team/schmidt-marie/).

On a fateful afternoon when I was still working on my PhD at the Rotterdam School of Management,
Niels Agatz entered my office and drew an interesting routing problem related to trucks and
drones on the whiteboard. It turned out he did the same with Marie Schmidt who was as much
inspired by the problem as I was, and a very interesting project was born.

In the project, we developed one of the earliest papers with an exact approach to solve a
Traveling Salesman Problem where locations can be visited by either a truck or a drone.
The drone has to be launched by the truck and has only carrying capacity for one parcel
before it has to come back to the truck to get a new payload. The drone can also stay
with the truck while the truck is moving around, and while the drone is out, the truck
can visit any number of locations. The drone can only meet up or leave the truck at
customer locations. The goal is to minimize the total time it takes to visit all
locations, either with the drone or the truck. The tricky part here is that the truck and
drone have to coordinate when they are together, which may induce additional waiting
time at locations.

A core idea we developed in our approach is an *operation*, which defines a starting
location where the drone and truck are together, an ending location where the drone
and truck are again together, and any number of intermediate locations of which one
can be visited by the drone, and the other locations are visited in a particular order by the
truck. It is assumed that travel times for the drone can be completely unrelated to the travel times
for the truck, although in our experiments we use a constant ratio for the sake of simplicity.

So far, two papers came out based on this work, of which one has received over
580 and over 200 citation according to Google Scholar in February 2023.

## Research Output

* [Optimization Approaches for the Traveling Salesman Problem with Drone](https://doi.org/10.1287/trsc.2017.0791) in *Transportation Science* (Volume 52, Issue 4, July 2018)
* [Dynamic programming approaches for the traveling salesman problem with drone](https://doi.org/10.1002/net.21864) in *Networks* (Volume 72, Issue 4, December 2018)
* [Drones-TSP: Traveling Salesman with Drone (Java code) v1.0.0](https://doi.org/10.1287/trsc.2017.0791). Java code used in our projects.
* [Instances for the TSP with Drone (and some solutions)](https://doi.org/10.5281/zenodo.1204676). Instances used in our experiments.