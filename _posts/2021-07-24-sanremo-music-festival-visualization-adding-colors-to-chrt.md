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

As you can see, this is not a standard chart: to create it we stacked five `.chrtPoint()` charts one on top of the other.

The first one shows an overview of how many male (blue) and female (magenta) professionals (hosts, assistants, producers, winners) worked in each edition of the festival. The x-axis represents the time (one edition each year, starting from 1951), while the y-axis represents the number for each gender.

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
    "x": Int,
    "ym": Int,
    "yf": Int,
    "yg": Int,
  },
]
```

Where `ym`, `yf`, and `yg` represent the number of males, females, and groups for each year.

The following charts show a breakdown of the data, each one representing one of the _professionalities_ included in the global  overview: hosts (_conduttori_), assistants (_co-conduttori_, or _vallette_), artistic directors (_direttori artistici_), and winners (_vincitori_).

![](/assets/uploads/screenshot-2021-07-30-at-10-58-43.png)

Chrt does not provide a built-in method to create _dot-strips_, but creating one with the tools we have it's pretty easy: **Each dot-strip is nothing more than a** `.chrtPoint()` **with a** `y` **value hardcoded to** `0`, and the radius of each point is proportional to the number we want to represent for that year.

This view allows us to better understand how genders are represented by role, highlighting some non-unexpected facts: women are _relegated_ to act as assistants, while **the roles of power** (like artistic director and host) **are dominated by men**. Note how in seventy years of history, there has been just one woman acting as artistic director.

From a code perspective creating these dot-strips is easy. After creating a chart, you can simply add the series, assigning the correct properties to each point:

```javascript
.add(
  chrt.chrtPoints()
  .data(points.map(d => ({ x: d.x, y: 0, ys: d.ym, })))
  .color(M)
  .radius(d => d.ys)
  .stroke(S)
  .strokeWidth(1)
)
```

In this case the data-source is different, and `d.ys` (the `.radius()` of each point) represents the number of persons of the currently selected gender over the total for each year. Each chart shows three separate series, one for each group. Overlapping items remain visible because I applied a `mix-blend-mode` CSS property to the discs.

The visualization is structured to have five Chrt `.chrtPoint()` charts one on top of the other. **Size, positions, and margins are defined via CSS in order to harmonize the different charts into one, large visualization**.

I hope you enjoyed reading how our plot about the Sanremo Music Festival has been created; I also hope this article gave you some idea on how to approach this kind of visualization. **For any comment or hint**, please feel free to reach us via Twitter: [@chrt_io](https://twitter.com/chrt_io "Chart.io on Twitter").