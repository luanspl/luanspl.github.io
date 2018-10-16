---
layout: post
title: Measurements Using a Respeaker On a Raspberry PI 3
date: 2018-03-09 00:00:00 +0800
description: You’ll find this post the project about measurements using a ResPeaker on a Raspberry PI 3 # Add post description (optional)
img: Respeaker_img_title.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Respeaker, Raspberry]
---

This project aims to record samples of different audios from a seeed ReSpeaker 4-mic Array on a Raspberry PI 3. The audio samples were recorded in different environments which it implies a different kind of noises, so we can make an estimation of noises with these samples.
The ReSpeaker has 4 microphones, in other words, 4 different channels, so we can explore the TDOA (Time Difference of Arrival) to find the transmitter location by comparing the difference of time in each channel. There are also samples of speech, so we can do the speaking tracking and others different processing projects using voice.


## Specifications
![ResPeaker]({{site.baseurl}}/assets/img/ReSpeaker_box.jpg)

Specifications:
* Specifications about the <a href="http://wiki.seeedstudio.com/ReSpeaker_4_Mic_Array_for_Raspberry_Pi/">ReSpeaker 4-mic Array </a>
* Specifications about the <a href="https://www.raspberrypi.org/products/raspberry-pi-3-model-b/">Raspberry PI 3 model B </a> 
* Specifications about the <a href="https://www.jbl.com/flip/JBL+FLIP+III.html?cgid=flip&dwvar_JBL%20FLIP%20III_color=Black-GLOBAL-Current">Source Sound (JBL FLIP 3) </a> 
* Operating System: Linux Ubuntu 16.04


## Controlled Measurements

![ResPeaker]({{site.baseurl}}/assets/img/controlled_measurements.jpg)

The Controlled Measurements are intended to obtain audio information from the ReSpeaker 4-Mic Array using the Raspberry Pi 3 for different analysis. The analysis results of the controlled measurements use data measures of two and four channels separately. The measures were made with distances and angles known, the distance range between source and microphone of 0.5 meters to 1.5 meters with a step of 0.5 meters, and the range angle was made between 0 degrees to 90 degrees with a step of 10 degrees.
The measurements environment were the NPIT lab in the UFRN, the closed laboratory has constant noises like Nobreaks computer, the measurements were made on the floor with the temperature approximatively 20º Celsius.

dimensions environment are approximatively (8.25 x 5.91) meters.

The source (JBL Flip 3) frequency is constant and deterministic (a tone - 1Khz), the conditions (environment) are approximately constant, and the sampling frequency is also constant.

<b>4 Channels Measurements </b>

![ResPeaker]({{site.baseurl}}/assets/img/measurements_4_channels.png)
The controlled measurements with four channels were realized in the know distance of 0.5, 1.0 and 1.5 meters away from the audio source. The measurements were made with reference in the MIC_3 from Respeaker recorded the all four channels.


<b>2 Channels Measurements </b>

![ResPeaker]({{site.baseurl}}/assets/img/measurement_2channel.png)

The controlled measurements with only two channels were made in the 0.5, 1.0 and 1.5 meters away from the audio source. The measurements were made with reference in the MIC_3 from Respeaker and recorded only the channel 1 and channel 2, MIC_1 and MIC_2 repectively.

Important Note: the audio files in .wav contains the four channels.


## Measurements in Different Scenarios

Analysis of different scenarios to verify different conditions and environments. 
The project about estimation noise using these measurements is in this <a href="">link</a>

the measurements were made in the scenario Auditorium NPIT, it is in a quite and calm place without large noises, the other scenario is Outside building NPITI, it is in loud place with a large noise and the measurments in this place were made in the side of a construction building and the third measurements were made in the Hall of the NPITI.

[...]





