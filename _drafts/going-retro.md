---
layout: post
title: Going Retro
date: 2021-06-28 22:00:00 +0000
categories: ''

---
The visual language of old data visualization always amazed me: being able to represent complex data with few elements and colors, and yet making it readable is an exciting challenge.

The web is full of different examples, [Nightingale](https://nightingaledvs.com), the online magazine from the [Data Visualization Society](https://www.datavisualizationsociety.org "DVS Website") has a lot of articles about the topic.

Recently, the work that[ W.E.B. Du Bois presented at the 1900 World Fair in Paris gained a lot of visibility](https://www.smithsonianmag.com/history/first-time-together-and-color-book-displays-web-du-bois-visionary-infographics-180970826/ "W.E.B. Du Bois’ Visionary Infographics Come Together for the First Time in Full Color"), even with the publication of a [monographic book](https://amzn.to/3x6IK0u "Visualizing Black America: The Color Line at the Turn of the Twentieth Century") with all his charts.

![COMPARATIVE RATE OF INCREASE OF THE WHITE AND NEGRO ELEMENTS OF THE POPULATION OF THE UNITED STATES - PRINCETON ARCHITECTURAL PRESS](/assets/uploads/screenshot-2021-06-29-at-19-41-22.png "COMPARATIVE RATE OF INCREASE OF THE WHITE AND NEGRO ELEMENTS OF THE POPULATION OF THE UNITED STATES - PRINCETON ARCHITECTURAL PRESS")

Another name that is often cited when talking about _Historical Data Visualization_ is [Charles Minard](https://en.wikipedia.org/wiki/Charles_Joseph_Minard "Charles Minard on Wikipedia"), who created the chart that someone calls [_The Best Graphic Ever Produced_](https://www.nationalgeographic.com/culture/article/charles-minard-cartography-infographics-history "The Underappreciated Man Behind the “Best Graphic Ever Produced”"), illustrating Napoleon's travel to Russia during his 1812 campaign.

![By Charles Minard (1781-1870), Public Domain](https://upload.wikimedia.org/wikipedia/commons/thumb/2/29/Minard.png/1600px-Minard.png "By Charles Minard (1781-1870), Public Domain")

To be clear: I'm not comparing the charts I'll show in few lines to these great examples of complex data visualizations; I'm just explaining why when I have been asked to test chrt, I chose to try to replicate this _retrò_ feeling.

## The data

We all know what happened at the end of 2019 in China, and how this impacted the lives of almost everyone in the world. The virus reached Italy, officially, on February 24th, 2020, when _Patient 0_ was identified. Starting from the following month, as soon as the [Italian Civil Protection](https://www.protezionecivile.gov.it/it/ "Dipartimento della Protezione Civile") released a [Github repo](https://github.com/pcm-dpc/COVID-19 "pcm-dpc/COVID-19") containing all the data, Visualize News, the collective of Data Visualization professionals I am part of,[ created a website](https://coronavirus.visualize.news "Corona Virus in Italy") whose goal was to explain the Corona Virus situation in Italy to foreigners. The fastest way to start using this new library was to reuse some data I already had.

## The Visualizations

As said, I chose to plot data regarding the Covid-19 epidemic in Italy. Both plots use _small multiples_ to compare the evolution over time.

The first one, shown here, uses multiple _bar charts_ to highlight the weekly progression of the virus in Italy. Each bar represents a week (as indicated by the labels at the very top and very bottom of the image): **all the charts share the same _x-axis_**, but they are independent regarding the _y-axis_: since the goal was to show a trend and not the actual numbers, I removed the labels and ticks of the vertical axis, **highlighting with an annotation the peak, and the type of data shown**. The last week shows, on top of the bar, an annotation showing the figures for that week.

![Weekly Covid-19 Progression in Italy since Jan. 1st, 2021](/assets/uploads/screenshot-2021-06-29-at-19-05-48.png "Weekly Covid-19 Progression in Italy since Jan. 1st, 2021")

As you can see, I avoided using colors, replacing them with SVG patterns: I've been able to assign a different pattern to each bar, depending on the quality of the data it represents (cross-hatched for _normal_ data, lines with a 45-degree inclination heading up for _higher_ values, lines with a 45-degree inclination heading down for _lower_ values of each category).

The second chart aims to show if the Covid-19 impact on our lives changed between 2020 and 2021. Each data point is a week; the light grey area is 2020, while the dark grey line is 2021. Again, I've been able to create a readable chart without the need to use any color.

![Weekly Progression of Covid-19 in Italy: Comparison Between 2020 and 2021](/assets/uploads/screenshot-2021-06-29-at-19-49-04.png "Weekly Progression of Covid-19 in Italy: Comparison Between 2020 and 2021")

At a closer inspection, you'll notice that the grey area is, in fact, a pattern.

![Detail of the Pattern](/assets/uploads/screenshot-2021-06-29-at-19-50-00.png "Detail of the Pattern")

## The code

How to create a new chart, and how to add data have been already shown in other posts. What I want to show here is how easy it is to add annotations, and _axis lines_ to highlight certain values.

Annotations are extremely important for charts, either to explain the series themselves (like in these two examples, where I omitted axis' titles) or to help better understand the meaning of the data.

With chrt, adding an annotation is as simple as

    chart.add(
          chrtAnnotation(`<div>${label}: ${new Intl.NumberFormat('en-EN').format(maxObj.value)}</div>`)
          .top(max)
          .left(maxIndex)
        );

Where `.top()` sets the **vertical** position, and `.left()` the horizontal position. The variables `max` and `maxIndex` are **values**, not pixels. chrt takes care of converting your values into coordinates based on the scale that you defined when you added the data.

And what about the markers ◉ visible in the second chart? And the position of the annotations? That's just a bit of CSS code. It is easy, in fact, to add a custom CSS class to the annotation object, and use `transform` rules and pseudo-classes to change the position and layout of each annotation:

    chart.add(
          chrtAnnotation(`<div>${label}:<br />${new Intl.NumberFormat('en-EN').format(maxObj.value)} Week of ${new Date(maxObj.datetime).getMonth() + 1}/${new Date(maxObj.datetime).getDate()}/${new Date(maxObj.datetime).getFullYear()}</div>`)
          .top(max)
          .left(maxObj.week)
          .class('marker')
          .class(position === 1 ? 'reverse' : 'normal')
        );

Here is the CSS:

    .chrt-annotation.marker:after {
    	bottom: -9px;
    	content: '⦿';
    	display: block;
    	font-size: 12px;
    	height: 12px;
    	left: 50%;
    	line-height: 12px;
    	position: absolute;
    	text-align: center;
    	transform: translate3d(-50%, 0, 0);
    }
    
    .chrt-annotation.marker.reverse:after {
    	bottom: auto;
    	top: -13px;
    	transform: translate3d(-50%, 0, 0);
    }

I use a `position` variable to choose if the annotation should be shown at the top or at the bottom of the data point, and then I'll change the position of the ◉ based on the CSS class name assigned.