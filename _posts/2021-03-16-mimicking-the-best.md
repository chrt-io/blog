---
layout: post
title: Mimicking the best
date: 2021-03-16 00:00:00 +0000
categories: ''

---
#### How can we create beautiful charts? Replicate the best!

From the first moment we used **chrt** to clone charts that we liked from leading publications and inspiring books. The principle was simple: if we can reproduce the charts produced by NYT, Washington Post, Economist and others with **chrt,** then we will cover most of the best practices of data visualization.

Another source of inspiration we used since day one is the [Datawrapper blog](https://blog.datawrapper.de/). We tried to replicate the charts from [Greenland’s ice is melting, but without an OMG moment](https://blog.datawrapper.de/weekly-chart-greenland-ice-melting-global-warming-2019/) (that is also an experiment inspired by a chart from the Economist).

The result was exciting 🎊:

![](/assets/uploads/screenshot-2021-06-27-at-18-04-26.png)

![](/assets/uploads/screenshot-2021-06-27-at-18-06-51.png)

These charts ☝️ made with **chrt** contain multiple elements:

* lines
* scatter plot
* areas with variable baseline
* inside and outside aligned labels
* label formatting

The first chart that we replicated with **chrt** is [The Productivity–Pay Gap](https://www.epi.org/productivity-pay-gap/) by the Economic Policy Institute:

![](/assets/uploads/screenshot-2021-06-27-at-18-46-55.png)

The chart replicated with **chrt** includes:

* annotations
* markers
* labels
* range indicator
* x axis in the middle of the chart

#### By mimicking the charts that we found well designed and interesting, we could implement quickly many of the features that we wanted in **chrt** with a focus on quality.