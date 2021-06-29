---
layout: post
title: Going Retro
date: 2021-06-28 22:00:00 +0000
categories: ''

---
The visual language of old data visualization always amazed me: being able to represent complex data with few elements and colors, and yet making it readable is an exciting challenge.

The web is full of different examples, [Nightingale](https://medium.com/nightingale "DVS Nightingale"), the online magazine from the [Data Visualization Society](https://www.datavisualizationsociety.org "DVS Website") has a lot of articles about the topic.

Recently, the work that[ W.E.B. Du Bois presented at the 1900 World Fair in Paris gained a lot of visibility](https://www.smithsonianmag.com/history/first-time-together-and-color-book-displays-web-du-bois-visionary-infographics-180970826/ "W.E.B. Du Bois’ Visionary Infographics Come Together for the First Time in Full Color"), even with the publication of a [monographic book](https://amzn.to/3x6IK0u "Visualizing Black America: The Color Line at the Turn of the Twentieth Century") with all his charts.

![COMPARATIVE RATE OF INCREASE OF THE WHITE AND NEGRO ELEMENTS OF THE POPULATION OF THE UNITED STATES - PRINCETON ARCHITECTURAL PRESS](/assets/uploads/screenshot-2021-06-29-at-19-41-22.png "COMPARATIVE RATE OF INCREASE OF THE WHITE AND NEGRO ELEMENTS OF THE POPULATION OF THE UNITED STATES - PRINCETON ARCHITECTURAL PRESS")

Another name that is often cited when talking about _Historical Data Visualization_ is [Charles Minard](https://en.wikipedia.org/wiki/Charles_Joseph_Minard "Charles Minard on Wikipedia"), who created the chart that someone calls [_The Best Graphic Ever Produced_](https://www.nationalgeographic.com/culture/article/charles-minard-cartography-infographics-history "The Underappreciated Man Behind the “Best Graphic Ever Produced”"), illustrating Napoleon's travel to Russia during his 1812 campaign.

![By Charles Minard (1781-1870), Public Domain](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Minard.png/1600px-Minard.png "By Charles Minard (1781-1870), Public Domain")

To be clear: I'm not comparing the charts I'll show in few lines to these great examples of complex data visualizations; I'm just explaining why when I have been asked to test chrt, I chose to try to replicate this _retrò_ feeling.

## The data

We all know what happened at the end of 2019 in China, and how this impacted the lives of almost everyone in the world. The virus reached Italy, officially, on February 24th, 2020, when _Patient 0_ was identified. Starting from the following month, as soon as the [Italian Civil Protection](https://www.protezionecivile.gov.it/it/ "Dipartimento della Protezione Civile") released a [Github repo](https://github.com/pcm-dpc/COVID-19 "pcm-dpc/COVID-19") containing all the data, Visualize News, the collective of Data Visualization professionals I am part of,[ created a website](https://coronavirus.visualize.news "Corona Virus in Italy") whose goal was to explain the Corona Virus situation in Italy to foreigners. The fastest way to start using this new library was to reuse some data I already had.

## The Visualizations

As said, I chose to plot data regarding the Covid-19 epidemic in Italy. Both plots use _small multiples_ to compare the evolution over time. The first one, shown here, uses multiple _bar charts_ to highlight the weekly progression of the virus in Italy. Each bar represents a week (as indicated by the labels at the very top and very bottom of the image): **all the charts share the same _x-axis_**, but they are independent regarding the _y-axis_: since the goal was to show a trend and not the actual numbers, I removed the labels and ticks of the vertical axis, **highlighting with an annotation the peak, and the type of data shown**. The last week shows, on top of the bar, an annotation showing the figures for that week.

![](/assets/uploads/screenshot-2021-06-29-at-19-05-48.png)