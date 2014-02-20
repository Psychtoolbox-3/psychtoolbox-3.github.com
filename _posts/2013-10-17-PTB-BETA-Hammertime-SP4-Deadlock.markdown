---
layout: post
title: PTB BETA "Hammertime!" - SP4 "Deadlock"
categories: news
author: kleinerm
---

This beta release fixes some ugly regression introduced into the PTB for Linux
in the last beta. The regression could cause a crash of Octave or Matlab when
quitting the application or clearing the `Screen` function on some setups with
some scripts.

It makes `DaqDeviceIndex` mildly more robust on 64-Bit OSX by applying a new set
of horrifiying hacks.

Fixes some small bugs in `IsomerizationIn[Eye/Dish]Demo` and makes them work on
Octave again, after some regression was introduced this summer.
