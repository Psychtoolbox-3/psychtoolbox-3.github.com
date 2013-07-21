---
layout: post
title: PTB beta “The fun in dysfunction” SP2 release 2013-1-14
categories: news
author: kleinerm
---

Git tag: `PTB_Beta-2013-01-14_V3.0.10`

This update is dedicated to Aaron Swartz (R.I.P.) and others who fight for freedom of information and the internet. It contains some improvements to M-Files.

All systems:
------------

* Full panelfitter high-level setup support via `PsychImaging('AddTask',
  'General', 'UsePanelFitter')`: Selection of common scaling/fitting modes.
  Fully compatible with all stereo display modes, high-precision display modes
  and other `PsychImaging` tasks. Also now fully compatible with
  `RemapMouse()`. 

* Cleanups to `BeampositionTest` by Ian A. 

* Robustness improvements to `GStreamer-SDK` detection on 64-Bit Windows. 

* Fix `PsychImaging` display mirroring when only fixed-function pipeline is active. 

* Tiny fixes in `moglmorpher()` and `LoadOBJFile()`. 

* Minor tweaks to some demos.
