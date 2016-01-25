---
layout: post
title: PTB BETA "Into Darkness" released
categories: news
author: kleinerm
---

The new BETA "Into Darkness" was released at 25th January 2016.

As usual, the complete development history can be found in our GitHub repository. The release tag is “PTB_Beta-2016-01-25_V3.0.12”, with the full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2016-01-25_V3.0.12>

### New features and improvements:

- FTGL Drawtext plugin support for MS-Windows. Used as default textrenderer 1 on Windows, with fallback to the GDI legacy renderer if it is unsupported. Requires use of Octave-4 on Windows, or in case of Matlab on Windows that GStreamer is installed. We now have a consistent high quality text renderer on all platforms. This should also fix HiDPI display issues with text rendering on Windows, give much better anti-aliased text quality, and better text positioning. On GitHub issues: Fixes #282 Fixes #254 

- The default text renderer 1 is now always the (originally Linux only) FTGL renderer. Screen('Preference','TextRenderer', 0) allows to select the OS specific legacy renderer (GDI on Windows, Apple CoreText on OSX). The legacy renderer is also used as fallback if the FTGL plugin fails for some reason. Note that use of the legacy renderer is from now on completely unsupported by us if you should run into any problems with it. It is on "life support" and may be removed completely in a future version of Psychtoolbox.

- Use same font ("Arial" or something close to it), text size (24 pixels), style (normal) by default on all operating systems instead of OS specific settings, now that we use the same text renderer by default on all OSes, so one size should fit all.

- Screen('DrawDots/DrawLines'): Add size limit queries and lenient flag. These functions now optionally return the min/max size of normal or anti-aliased dots and lines for the given graphics card/driver, as those differ across gpu's, drivers and operating systems.

- Minor other improvements.

### Bug fixes:

- Fix fast offscreen window support on use of PsychImaging 'UseRetinaDisplay'. Was accidentally falling back to the old more limited legacy implementation if Retina support was requested.
- Screen('GetImage') - Make sure 'rect' is inside the source window.
- Textbounds() - Accept optional 'yPositionIsBaseline' flag and make more robust. Contributed by Denis Pelli.
- OffsetRect: Resolve ambiguity for 4x4 'oldrect' matrix. Contributed by GitHub user mscain.
- Snd(): Make more robust against failing InitializePsychSound().
