---
layout: post
title: PLC - Industrial Automation
date: 2017-06-15 00:00:00 +0500
description: Simple project about industrial automation using PLC # Add post description (optional)
img: PLC_title.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [PLC, Ladder, Graficet, Industrial, Automation]
---


There are subjects in the industrial automation field as switching engines (Redundancy) and engine failure operations (Fault Tolerance) which are essential.


## PLC

![PLC]({{site.baseurl}}/assets/img/PLC.jpg){:height="450px" width="45%" style="display: block; margin: 0 auto"}

## Redudancy

Redundancy is to use duplicated equipment and switching them eventually, while the primary is active, the other is inactive. 
 The advantages of Redundancy is to improve the availability of station and switching them, it can increase the equipment lifetime.

 
For example, some water supply distribution company has four engines which two engines are bigger (Q1 and Q4) and the others two are smaller (Q2 and Q3), 
 so the company wants only one bigger engine and one smaller working at once, the others two are the redundancy in case of failure.
 
The switching control can be made by programming rising and falling edge detection, so in this case, there will be four switching modes using two internal coils with rising edge detection.

The following table shows the switching mode configuration. M1(p) and M2(p) are the internal coal with rise edge detection.
 S1 to S4 are the switching modes witchThe following table shows the switching mode configuration. M1(p) and M2(p) are the internal coal with rising edge detection. S1 to S4 are the switching modes which will combine the engines.

| M1(p) | M2(p) | Switching Mode | Engines |
| 1 | 1 | S1 | Engine 1 AND 2 |
| 0 | 1 | S2 | Engine 1 AND 3 |
| 1 | 0 | S3 | Engine 4 AND 3 |
| 0 | 0 | S4 |Engine 4 AND 2 |


![PLC]({{site.baseurl}}/assets/img/wave_PLC_1.png){:height="450px" width="60%" style="display: block; margin: 0 auto"}

<p align="center">
<b>Switching mode timing diagram.</b>
</p>
 
## Fault Tolerance

Fault tolerance uses duplicated equipment not only to improve the availability of station, but also to eliminate bad signals going to the field due to hardware failure.
 The fault can be observed with the help of alarm and seen on the SCADA, and also it can automatically stop the engine or switch it.
 The fault could be anything to prevent something to make an engine does not work properly, it depends on the project.

<h3><b>Graficet</b></h3> 

As an example a simple project of two engines, they can switch automatically in case of failure.

![PLC]({{site.baseurl}}/assets/img/Grafcet_Failure.png){:height="450px" width="50%" style="display: block; margin: 0 auto"}

<p align="center">
<b>Simple example of failure operation</b>
</p>


At this example there are two counters and two timers, if the engine does not work, after three tries, then it switches to other engine and shows the failure engine alarm.

 
 
 
 