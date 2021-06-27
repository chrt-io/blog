---
layout: post
title: How does a chrt should look like?
date: 2021-02-16 00:00:00 +0000
categories: ''

---
#### At **chrt** we are always very excited 👯 when we create new charts 📊. We love _neat and crisp_ 🤓 charts 📈.

The big names 🧑‍🏫 👩‍🏫 (Spear, Bertin, Wilkinson, Tukey, Few, Tufte and others) have all described the best practices long ago, and still for most of the charts that we see out in the wild 🦁 (literally in the wild) it seems like they have never known about the existence of these practices.

#### Luckily the wilderness 🦁 is not that wild 🐱

There are examples of libraries and tools to generate inspiring beautiful charts. One of our favourite tool is [Datawrapper](https://www.datawrapper.de/), leading publications build charts with it. Datawrapper won't let you disappointed: the charts are beautiful, neat and easy to read - and they follow the best practices. I would say that in a way they are _opinionated charts_: datawrapper lets you customize almost everything without destroying years of research in data visualization with some questionably designed chart element (axis titles, annotations, labels...)

This doesn't quite often happens with chart libraries, throug which you can do almost everything. I will never forget the feeling when I stepped into the pavillion of a large conference to see all around me dashboards built with the default versions of some widely used chart libraries. Default colors, default fonts, default sizes, rotated titles and labels...everywhere around me. I thought: _why default charts should not be beautiful?_ and _why default charts should be so tough to customize?_ and ultimately _crafting charts should be fun!_

Whit this question in minds we set out our first goals for **chrt**:

* neat and crisp ✨
* following best practices 📚🎓
* easy to customize 💇

The answer to these questions is another question:

#### How to set the right balance between opinionated logic and flexibility?

As developers we want the freedom to control every pixel of our screen, as designers we want to define boundaries. We will need to figure out where **chrt** is sitting between these two approaches.