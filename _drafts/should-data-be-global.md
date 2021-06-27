---
layout: post
title: Should data be global?
date: 2021-03-03 00:00:00 +0000
categories: ''

---
Most of the approaches of chart libraries expect the developer to declare the data for the entire chart. The paper [A layered grammar of graphics](http://vita.had.co.nz/papers/layered-grammar.html) states: 

> When creating a plot we start with data.

This is the mantra 🙏 of data visualization: first learn about your data, then decide how to visualize it. We agree with that! But from a programming standpoint, could it be more casual? Do we really need to start from the data?

#### What if at a logic level the data is local to the visual item that shows it?

With **chrt** we thought that together with the more traditional approach of declaring the data at a chart level:

    Chrt().data([...])

We could alsot declare the data directly from the component that uses it and let chrt manage the data internally 🪄:

    Chrt()
    	.add(chrtColumns().data([...])
        .add(chrtLine().data[...])

With this approah we can dinamically add components to the chart.