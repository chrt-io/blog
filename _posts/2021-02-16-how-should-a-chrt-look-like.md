---
layout: post
title: How should a chrt look like?
date: 2021-02-16T00:00:00.000+00:00
categories: ''
author: Carlo Zapponi
post_categories: Blog
twitter_handle: "@littleark"
seo_and_social_networks:
  description: At chrt we are always very excited when we create new charts. We love
    neat and crisp charts.
  keywords: chrt, chrt.io
  banner_image: "/assets/uploads/screenshot-2021-06-27-at-18-06-51.png"

---
#### At **chrt** we are always very excited 👯 when we create new charts 📊. We love _neat and crisp_ 🤓 charts 📈.

The big names 🧑‍🏫 👩‍🏫 (Spear, Bertin, Wilkinson, Tukey, Few, Tufte and others) have all described the best practices long ago, and still, for most of the charts that we see out in the wild 🦁 (literally in the wild), it seems like they have never known about the existence of these practices.

#### Luckily the wilderness 🦁 is not that wild 🐱

There are examples of libraries and tools to generate inspiring beautiful charts. One of our favourite tools is [Datawrapper](https://www.datawrapper.de/). Datawrapper won't let you disappointed: the charts are beautiful, neat and easy to read - and they follow the best practices. I would say that in a way they are _opinionated charts_: as a user, you can customize almost everything without wrecking years of research in data visualization with some questionably designed chart element (axis titles, annotations, labels...)

This doesn't quite often happen with chart libraries, through which you can do almost everything. I will never forget the feeling when I stepped into the pavilion of a large conference to see all around me dashboards built with the default versions of some widely used chart libraries. Default colors, default fonts, default sizes, rotated titles and labels...everywhere around me. I thought: _why default charts should not be beautiful?_ and _why default charts should be so tough to customize?_ and ultimately _crafting charts should be fun!_

Whit this questions in mind we set out our first goals for **chrt**:

* neat and crisp ✨
* following best practices 📚🎓
* easy to customize 💇

The answer to these questions led to another question:

#### How to set the right balance between opinionated logic and flexibility?

As developers we want the freedom to control every pixel of our screen, as designers, we want to define boundaries. We will need to figure out where **chrt** is sitting between these two approaches.