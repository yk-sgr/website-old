---
author: Yannick Seeger
title: "How I reduced Flutter boilerplate code"
date: 2021-08-21T18:00:24+02:00
description: How to reduce boilerplate code in your flutter app.
tags: ["programming", "flutter"]
summary: How to reduce boilerplate code in your flutter app.
---

First of all: I am definitely not a Flutter professional. But over the years I’ve gained a lot of experience with other programming languages. To cut right to the chase: When I first looked at Flutter, I disliked the amount of boilerplate code.

---

# 1. Routing
[auto_route](https://pub.dev/packages/auto_route) is a great package. Using code generation, auto_route helps set up the routing of the app in a few lines. I actually don’t like the Navigation 2 approach of Flutter (at least when I set it up myself), but that’s no problem at all with auto_route.

# 2. State Management
There are a lot of state management packages out there. But I recommend [riverpod](https://pub.dev/packages/riverpod), though. At the time of writing, pre-release 1.0 is out, but unfortunately the documentation is not quite up to date. However, it does save a lot of time writing boilerplate code.
Maybe I’m going to extend this list in the future. But I really wanted to share my thoughts about these packages.

Happy Coding!