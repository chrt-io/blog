---
layout: post
title: The unfolding of chrt
date: 2021-02-02T00:00:00.000+00:00
categories: ''
author: Carlo Zapponi
twitter_handle: "@littleark"
seo_and_social_networks:
  description: The system I was thinking about had to be simple, intuitive and with
    default settings to build beautifully crafted charts. Yes, beautifully crafted.
  keywords: chrt, history, foundation
  banner_image: "/assets/uploads/logo.png"
post_categories: Blog

---
When I used [Scratch](https://scratch.mit.edu/) with my daughter, I noticed how intuitive is thinking in blocks (and nested blocks), and I wondered why we were not building charts similarly with javascript. It was fun and it helped to ideate through one of the most natural process: _addition_.

I thought that creating charts could be as simple as plugging blocks one after the other (or inside each other):

* add a chart canvas block
* add a line chart block
* add an axis block
* ...and so on...

Yep! A system like this could be easily translated into Scratch blocks, or in more traditional programming languages:

    chart.add(linechart).add(axis)

The [layered grammar of graphics]() at the foundation of ggplot2 is based on a similar model. And I love it! However, ggplot2 is for R, it has a steep learning curve and can be tricky to visually customize.

The system I was thinking about had to be simple, intuitive and with default settings to build beautifully crafted charts. Yes, _beautifully crafted._ I've experimented with many chart libraries and I still have to find one that is easy to customize and that enforces the best practices (yes, I'm talking to you, rotated axis titles!).

#### The goal was outlined: a block-based javascript library to create beautiful charts in a fun way.

And that's how **chrt** started