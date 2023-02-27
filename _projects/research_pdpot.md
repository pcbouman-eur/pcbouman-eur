---
layout: project
title:  Online transfers
description: Pickup and delivery with online transfers
img: assets/img/research_pdpot.png
img_title: A prototype POD developed by NEXT future mobility
img_alt: A prototype POD developed by NEXT future mobility
importance: 1
category: research
---

This project is joint work with [Gizem (Özbaygın) Tiniç](https://sites.google.com/view/gizemozbaygin),
[Luuk Veelenturf](https://www.rsm.nl/people/luuk-veelenturf) and
[Rick Willemsen](https://www.erim.eur.nl/people/rick-willemsen/).

This research is partly inspired by a novel mobility concept called *NEXT Future Transportation*. We have developed a MIP-based optimization model that allows us to 
solve a pick-up and delivery problem where passengers can both transfer en-route when vehicles are platooning, as well as transfer by leaving one vehicle,
waiting for another vehicle to arrive and then entering the other vehicle.
We still have to finish writing our paper on the optimization and modelling.

<iframe width="560" height="315" src="https://www.youtube.com/embed/kJlQaCIUHTI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<br />

## Description

Recently there is increasing attention in the literature for more flexible and autonomous ways of public transportation.
Some focus on semi-flexible public transportation. Examples are systems with a mix of conventional taxis and timetabled shuttle busses, limiting the number of transfers in a transit system with a large number of vehicles, and integrating fixed routes with a general pickup and delivery problem.

In this research, we focus on full flexible passenger transportation. This can be considered as a variant or extension of the Dial-a-Ride Problem (DARP). The focus of the DARP is to bring passengers from their origin to their destination (e.g. the classical taxi problem). In later variants of this problem shared door-to-door services were investigated, to see the effect of allowing for multiple passengers (with different origins and destinations) to share the ride. We want to go one step further and look at the effects of allowing for transfers of passengers in such a shared door-to-door service, both *online* transfers that take place within two driving vehicles that are platooning, as well as by using *outside* transfers. 

The use of transfers in passenger transportation is not new. In public transport, it is one of the aspects that is typically considered when making a line plan. In logistics delivery services, transferring goods between vehicles at cross-docks or hubs is already quite common. In courier type of services we see transfers of passengers. However, these approaches mostly consider transfers at fixed predefined locations. In some of these approaches vehicles need to be synchronized, i.e. at the same location at the same time, to transfer the goods from one delivery vehicle to another, and in other approach this might not be required as temporary storage is allowed so a vehicle can leave goods for another vehicle to pickup later.

In order to investigate the potential of *online* transfers (i.e. while moving) in shared door-to-door services, many modelling tricks commonly used in the Dial-a-Ride Problem break down. Typically the only information about the road network that is required are distances between pickup and delivery locations, and in extensions of locations where transfers are possible. In case of online transfers, the actual topology of the road network is required, as facilitating an online transfer between two vehicles requires that both vehicles share the same road segment at the same point in time, even though the previous and next pickup and delivery locations are completely distinct. While many models for the Dial-a-Ride Problem focus on the sequence of the pickups and deliveries of the customers, online transfers require an integrated approach that takes the exact routes, timing included, of both passengers and vehicles into account.

In our research, we consider a Mixed Integer Program (MIP) to solve this problem, that can either be solved directly for small instances, or provide the basis for a heuristic in medium sized instances. We also develop a related column generation approach, and perform extensive computational experiments. Finally, we provide a number of analytical insights into the possible advantage of allowing online transfers, but these are omitted from this extended abstract for reasons of brevity.

More information can be read in the [extended abstract submitted to the TRISTAN 2022 Conference](https://tristan2022.org/Papers/TRISTAN_2022_paper_4450.pdf)