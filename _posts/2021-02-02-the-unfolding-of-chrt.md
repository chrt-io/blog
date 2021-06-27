---
layout: post
title: The unfolding of chrt
date: 2021-02-02 00:00:00 +0000
categories: ''

---
When I finally used [Scratch](https://scratch.mit.edu/) with my daughter, I started thinking in blocks (and nested blocks), and I wondered why we were not building charts similarly. It was fun and it helped to ideate through one of the most natural processes: _adding_.

I started to tinker away to create charts that could be as simple as plugging blocks one after the other (or inside each other):

* add a chart canvas block
* add a line chart block
* add an axis block
* ...and so on...

Yep! Something like this could be easily translated into Scratch blocks, or in more traditional programming languages:

    chart.add(linechart).add(axis)

It had to be simple, intuitive and with default settings that could build beautifully crafted charts. Yes, _beautifully crafted,_ because I've experimented with chart libraries since ever and I have to say they all need a significant effort to be customized or even to follow some of the best practices (I'm talking to you, rotated axis titles!).

So the goal was outlined: a block-based javascript library to create beautiful charts in a fun way.

And that's how **chrt** started