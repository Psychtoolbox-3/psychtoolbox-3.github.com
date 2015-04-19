---
layout: post
title: PTB BETA "Gifts for the gifted" SP1 released
categories: news
author: kleinerm
---

The new BETA "Gifts for the gifted" SP1 was relased at 19th April 2015.

As usual, the complete develoment history can be found in our GitHub
repository. The release tag is "PTB_Beta-2015-04-19_V3.0.12", with the
full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-04-19_V3.0.12>

### New features and improvements:

- SetMouse multi-screen improvements for Windows. Allow positioning relative to screen origin, as the screenNumber is now also honored on Windows.
- CMUBox doc updates for Windows. Describe how FIFO size must be set on Windows COM ports for good timing.
- KbQueue fixes for OSX. Avoid hang of scripts in KbQueueRelease on some OSX setups.
- PsychPortAudio improvement for Linux. Try to avoid selecting HDMI/DP audio on video outputs of graphics cards as default sound card. Prefer regular sound cards over graphics cards with sound output if possible.
- Handle Intel ddx DRI2 triple-buffering on Linux, so visual timing works on Intel graphics chips without need for special xorg.conf settings or ddx drivers. It is now possible to even take advantage of triple-buffering with properly adapted scripts.
- General improvements to timing checks on advanced operating systems which support OS native timestamping mode 4.
- Documentation updates.
- Fixes and refinements to demos.
- New function CenterRectArrayOnPoint() contributed by Natalia Zaretskaya.
- QuestQuantile() improvements by Denis Pelli.
- Some improvements to color calibration routines by David Brainard.
- Improvements for efficiency of clut updates and of error handling on VPixx devices.
- Some compatibility updates to joystick configuration files for current Linux distributions.
