---
layout: post
title: PTB BETA FlowerPower released
categories: news
author: kleinerm
---

This one is just a bug fix for the FlowerPower beta 3 days ago.

It fixes some locking bugs introduced into the Linux PTB by the last release,
which only affect use of FOSS graphics drivers with frame-sequential stereo or
async flips. Those fixes could have caused a deadlock in those use cases.

This release was successfully tested against the upcoming Ubuntu 13.10 "Saucy
Salamander" release.
