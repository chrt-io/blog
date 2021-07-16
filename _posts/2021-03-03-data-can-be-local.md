---
layout: post
title: Data can be local
date: 2021-03-03T00:00:00.000+00:00
categories: Blog
author: Carlo Zapponi
post_categories: Blog
twitter_handle: "@littleark"
seo_and_social_networks:
  description: How to assign data to series in your chrt chart
  keywords: 'data, chrt.io, chrt, '
  banner_image: ''

---
Most of the chart libraries expect the coder to declare the data for the entire chart. The paper [A layered grammar of graphics](http://vita.had.co.nz/papers/layered-grammar.html) states:

> When creating a plot we start with data.

At the same time, it defines layers as:

> each layer having one geometric object, one statistical transformation, one position adjustment, and optionally, one dataset and set of aesthetic mappings

And this is where we like ❤️‍🔥 the layered grammar.

###### At the logic level, data can be local to the visual item that shows it.

With **chrt** we followed the principle that together with the more traditional approach of declaring the data at a chart level:

    Chrt().data([...])

We can also skip compltely the data first and declare it directly with the component that uses it and let **chrt** manage the data internally 🪄:

    Chrt()
        .add(chrtColumns().data([...])
        .add(chrtLine().data[...])

With this approach we can dinamically add components to the chart with their own data:

    Chrt()
      .add(xAxis())
      .add(yAxis())
      .add(
        chrtLine()
          .data([2,3,6,10,23,5])
      )
      .add(
        chrtLine()
          .data([6,3,7,2,5,7,10,22,40,22])
      )

In the above ☝️ code snippet, we are adding two lines 📈 in the chart with their own set of data 📦, **chrt** will take care of updating scales and axes based on the combination of the two datasets as shown below (and yes! **chrt** works in [Observable](https://observablehq.com/) 🎊):

![](/assets/uploads/localdata.gif)

#### It will be completely up to the developers to decide if the data will be _centralized_ or _decentralized_