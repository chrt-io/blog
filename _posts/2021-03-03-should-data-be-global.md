---
layout: post
title: Data should be local
date: 2021-03-03 00:00:00 +0000
categories: ''

---
Most of the approaches of chart libraries expect the developer to declare the data for the entire chart. The paper [A layered grammar of graphics](http://vita.had.co.nz/papers/layered-grammar.html) states:

> When creating a plot we start with data.

This is the mantra 🙏 of data visualization: ☝️ first learn about your data, ✌️ then decide how to visualize it. We agree with that 😺! But from a programming standpoint, could it be more casual? Do we really need to start from the data?

#### What if at the logic level data is local to the visual item that shows it?

With **chrt** we thought that together with the more traditional approach of declaring the data at a chart level:

    Chrt().data([...])

We could also declare the data directly from the component that uses it and let **chrt** manage the data internally 🪄:

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

In the above ☝️ code snippet we are adding two lines 📈 in the chart with their own set of data 📦. **chrt** will take care of updating scales and axes based on the combination of the two datasets as shown below (and yes! **chrt** works in [Observable](https://observablehq.com/) 🎊):

![](/assets/uploads/localdata.gif)