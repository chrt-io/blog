---
layout: post
title: The inception of chrt
date: 2021-02-02 00:00:00 +0000
categories: ''

---
When I helped my daughter learn [Scratch](https://scratch.mit.edu/ "Scratch") I started thinking in blocks (and nested blocks), and I wonder why I could not create charts in a similar way. It was fun and it helped ideation by adding.

I thought if we could have a similar model for programming, then I realized I was already doing it everyday with any markup language (html,  xml and also React/JSX for the same matter).

Still it wasn't fun. I started to think about a way to create charts that could be simple as plugging blocks one after the other (or inside eachother): 

* add a chart canvas block
* add a line chart block
* add an axis block
* ...and so on...

Yep! Something that could be easily translated into Scratch blocks, and in more traditional programming languages:

    chart.add(linechart).add(axis)

It had to be simple, intuitive and with default settings that could build beautifully crafted charts. 

And that's how chrt was incepted.