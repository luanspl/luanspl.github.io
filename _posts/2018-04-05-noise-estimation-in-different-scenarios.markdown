---
layout: post
title: Noise Estimation in Different Scenarios
date: 2018-04-05 00:00:00 -0300
description: Gaussian and Non-Gaussian noise estimation in different scenarios. # Add post description (optional)
img: noise_estimation_title.png # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Estimation, Noise, Gaussian, Alhpa-Stable, Mix-Gaussian]
---

This project aims to estimate the different noise models, Gaussian and Non-Gaussian models (Gaussian Model, Alpha-Stable Model, Mix-Gaussian Model) 
in different Scenarios (Auditorium, Outdoor, Hall) and compare them. the collection of data audios to analysis were realized in the Federal University of Rio Grande do Norte (UFRN) at the NPITI lab, 


these are the results plots of each scenario, the histogram, Power Spectral Density (PSD), time and frequency domain of the first channel datas and of each kind of estimation.


## AUDITORIUM NPITI

<h3><b>Environment</b></h3>

This environment is the NPITI's auditorium which is a indoor with soundproof. It's a place where the UFRN's teachers and students can lecture, So it's a normal and quite place without large noises.

| <b>Auditorium NPITI</b> ![ResPeaker]({{site.baseurl}}/assets/img/scenarios/auditorium_1.jpg){:height="252px" width="50%" style="display: block; margin: 0 auto"} | 

<h3><b>Data Analysis</b></h3>

| <b>Histogram</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_channels_auditorium_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>PSD</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_channels_auditorium_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>Time and Frequency Domain</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/time_FFT_auditorium_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} |


<h3><b>Normal Estimation</b></h3>

<b>Normal distribution parameters:</b>

> mu=0.0000446289

> sigma=0.0039705515

| <b>Histogram Gaussian Estimation</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_gaussian_auditorium_afternoon_NPITI_gaussian_noise_plot.png){:height="252px" width="100%"} | <b>PSD Gaussian Estimation</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_gaussian_auditorium_afternoon_NPITI_gaussian_noise_plot.png){:height="252px" width="100%"} | 

<h3><b>Alpha-Stable Estimation</b></h3>


<b>Alpha stable parameters:</b>


> alpha=1.9872

> beta=0.3390

> gamma=0.0027

> delta=0.0000



| <b>PSD Auditorium Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_auditorium_alpha_stable.png){:height="252px" width="100%"} | <b>PDF Auditorium Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/pdf_auditorium_alpha_stable.png){:height="252px" width="100%"} | <b>Histogram Auditorium Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_auditorium_alpha_stable.png){:height="252px" width="100%"} |



<h3><b>Gaussian Mixture Estimation</b></h3>


<b>Parameters of the Gaussians:</b>

> Mu1: -0.0011067

> Sigma1: 0.0036058

> Mu2: 0.0013198

> Sigma2: 0.0035814

| <b>Gaussians of Mix-Gaussian Auditorium:</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/mix_gaussian_auditorium_1.png){:height="252px" width="100%"} | <b>Gaussians Sum of Mix-Gaussian Auditorium:</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/mix_gaussian_auditorium_2.png){:height="252px" width="100%"} | 

we can see that for quite places the normal distribution is better.

## OUTDOOR NPITI

<h3><b>Environment</b></h3>

This environment is outside of the NPITI building, so it's an outdoor environment and also a parking lot. There was construction next to the collection data equipment (Respeaker-Raspberry). Therefore it's a loud place with significant noises.

| <b>Outdoor NPITI</b> ![ResPeaker]({{site.baseurl}}/assets/img/scenarios/outside_1.jpg){:height="252px" width="100%"} | <b>Outdoor NPITI</b> ![ResPeaker]({{site.baseurl}}/assets/img/scenarios/outside_2.jpg){:height="252px" width="100%"} | 

<h3><b>Data Analysis</b></h3>

| <b>Histogram</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_channels_outside_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>PSD</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_channels_outside_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>Time and Frequency Domain</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/time_FFT_outside_afternoon_NPITI_noise_plot.png){:height="252px" width="100%"} |

<h3><b>Normal Estimation</b></h3>

<b>Normal distribution parameters:</b>


> mu=3.792169e-05

> sigma=4.744719e-02

| <b>Histogram Gaussian Estimation</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_gaussian_outside_afternoon_NPITI_gaussian_noise_plot.png){:height="252px" width="100%"} | <b>PSD Gaussian Estimation</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_gaussian_outside_afternoon_NPITI_gaussian_noise_plot.png){:height="252px" width="100%"} |


<h3><b>Alpha-Stable Estimation</b></h3>
*building open-field environment

<b>Alpha stable parameters:</b>


> alpha=1.2670

> beta=0.0051

> gamma=0.0167

> delta=0.0002


| <b>PSD Outdoor Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_outside_alpha_stable.png){:height="252px" width="100%"} | <b>PDF Outdoor Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/pdf_outside_alpha_stable.png){:height="252px" width="100%"} | <b>Histogram Outdoor Alhpa-Stable </b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_outside_alpha_stable.png){:height="252px" width="100%"} |


<h3><b>Gaussian Mixture Estimation</b></h3>


| <b>Gaussians of Mix-Gaussian Outdoor:</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/mix_gaussian_outside_1.png){:height="252px" width="100%"} | <b>Gaussians Sum of Mix-Gaussian Outdoor:</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/mix_gaussian_outside_2.png){:height="252px" width="100%"} |

we can see that for laud places the normal distribution is worse and the alpha-stable is better.

## HALL NPITI

<h3><b>Environment</b></h3>

This environment is inside of the NPITI building and the collection of datas had been made by the night, so there aren't so much noise, but there are reverberation because of the halls.

| <b>Hall NPITI</b> ![ResPeaker]({{site.baseurl}}/assets/img/scenarios/hall_1.jpg){:height="380px" width="100%"} | <b>Hall NPITI</b> ![ResPeaker]({{site.baseurl}}/assets/img/scenarios/hall_2.jpg){:height="380px" width="100%"} | 

<h3><b>Data Analysis</b></h3>

| <b>Histogram</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/histogram_channels_hall_night_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>PSD</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/psd_channels_hall_night_NPITI_noise_plot.png){:height="252px" width="100%"} | <b>Time and Frequency Domain</b> ![ResPeaker]({{site.baseurl}}/assets/img/estimation/time_FFT_hall_night_NPITI_noise_plot.png){:height="252px" width="100%"} |


## Conclusion

This project was about the characterization of the noise and how
it works in every signal to have the better characterization for
any situation. Every environment is specific and needs to have
a particular representation of the noise in every single case.

