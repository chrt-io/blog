---
layout: post
categories: Blog
tags:
- data visualization
- sanremo
- festival di sanremo
- music
- entertainment
- chrt
author: Simone
title: 'Sanremo Music Festival: adding colors to chrt'
date: 2021-07-24T22:00:00.000+00:00
seo_and_social_networks:
  description: With some creativity it is possible to use chrt to create unusual charts.
    This article describes how we used chrt to show gender diversity in the Sanremo
    music festival.
  banner_image: "/assets/uploads/screenshot-2021-07-27-at-14-36-43.png"

---
The [Sanremo Music Festival](https://en.wikipedia.org/wiki/Sanremo_Music_Festival "Sanremo Music Festiva on Wikipedia") is an important mundane event in Italy since the 1950s. Every year, soon after the Christmas break is over, new singers and old _chanteurs_ gather in Sanremo, for a week-long competition.

The Festival has been the first real _televised_ pop event in Italy, and it's an important part of Italian pop culture. During its seventy-years history, Sanremo's stage hosted almost all the top Italian pop singers, [Eurovision](https://en.wikipedia.org/wiki/Eurovision_Song_Contest "Eurovision Song Contest on Wikipedia") winners, and a lot of foreign guests (including Louis Armstrong, Elton John, Eminem, REM, Queen, and many others).

Traditionally, the event is hosted by a famous anchorman helped by one or more _vallette_ (the [definition of this word](https://www.treccani.it/vocabolario/valletta/ "Definition of Valletta"), in the Treccani dictionary, can be roughly translated as "young anchorman's female assistant"). What we want to understand, with this visualization, is if the 2017's [ #metoo](https://en.wikipedia.org/wiki/Me_Too_movement "Me Too on Wikipedia") movement changed the balance between genders in this very important event.

![Gender representation in the Sanremo Music Festival](/assets/uploads/screenshot-2021-07-27-at-15-13-41.png "Gender representation in the Sanremo Music Festival")

As you can see, this is not a standard chart: to create it we stacked four `.chrtPoint()` charts one on top of the other.

The first one shows an overview of how many male (blue) and female (magenta) professionals (hosts, co-hosts, producers, winners) worked in each edition of the festival. The x-axis represents the time (one edition each year, starting from 1951), while the y-axis represents the number for each gender.

![](/assets/uploads/screenshot-2021-07-29-at-16-59-13.png)

The missing y-axis labels are replaced with annotations, that highlight the most important data, giving some context.

![](/assets/uploads/screenshot-2021-07-29-at-17-02-44.png)This helps us to highlight one of the many inconsistencies in the story of the Festival: 2019 has been the year with the higher number of women (nine), but all of them were _vallette_.

Creating a `.chrtPoint()` chart is easy, and can be done in few simple steps.

First, you create a chart, and define its global properties:

```javascript
    const chart = new chrt.Chrt()
      .node(document.querySelector('#global'))
      .svg()
      .size(900, 250)
      .margins({
        bottom: 0,
        left: 0,
        right: 0,
        top: 35,
      }).padding({
        bottom: 10,
        left: 30,
        right: 30,
        top: 10,
      })
```

And then, you simply add a `.chrtPoint()` specifying your data source, and how to use it:

```javascript
chart.add(
  chrt.chrtPoints()
  .data(points.map(d => ({ x: d.x, y: d.ym, })).filter(d => d.y > 0))
  .color(M)
  .radius(5)
  .stroke(S)
  .strokeWidth(1)
).add(
  chrt.chrtPoints()
  .data(points.map(d => ({ x: d.x, y: d.yf, })).filter(d => d.y > 0))
  .color(F)
  .radius(5)
  .stroke(S)
  .strokeWidth(1)
).add(
  chrt.chrtPoints()
  .data(points.map(d => ({ x: d.x, y: d.yg, })).filter(d => d.y > 0))
  .color(G)
  .radius(5)
  .stroke(S)
  .strokeWidth(1)
);
```

I created a separate `.chrtPoint()` for each series, in order to make it easier to customize the point's `.color()`. My data-source has the following format:

```json
[
  {
  	x: [Integer],
    ym: [Integer],
    yf: [Integer],
    yg: [Integer],
  },
]
```

Where `ym`, `yf`, and `yg` represent the number of males, females, and groups for each year.

The following charts show a breakdown of the data, each one representing one of the _professionalities_ included in the global  overview: hosts (_conduttori_), assistants (_co-conduttori_, or _vallette_), artistic directors (_direttori artistici_), and winners (_vincitori_).