---
layout: post
title: PTB beta released 4.9.2010 (SVN Revision 1783)
categories: news
author: kleinerm
---

This summarizes all new beta features from 6.6.2010 up to 4.9.2010. [The
list of improvements is likely incomplete as always. For detailed logs,
click this
link](http://svn.berlios.de/wsvn/osxptb/beta/?op=log&rev=0&sc=0&isdir=1).

This update contains a couple of bug fixes and minor improvements. Most
interesting should be the improvements to the Eyelink toolbox by Frans
Cornelissen.

### Eyelink toolbox

-   Improvements and cleanup to many demos by Frans Cornelissen. Frans
    also enabled the video feed from the Eyelink eye camera during
    tracker calibration by default, so the subjects eye can be monitored
    during calibration procedures. The `PsychHardware/EyelinkToolbox/`
    folder contains a file “compatibility” (`help compatibility`) with
    information on what has changed in this release of the Eyelink
    toolbox and how to restore the old behaviour if you don’t like the
    eye camera video feed to be displayed.

### `PsychPortAudio` sound driver

-   Bugfix when used with Microsoft Windows Vista or Windows-7 on fast
    multi-core machines (e.g., has only been observed on a 8 core, 2.7
    Ghz PC running Windows-7): Under certain circumstances the driver
    may falsely report your computers clock to be broken (“Time going
    backwards” warning) and switch to a low resolution backup clock.
    This is now fixed. The same fix applies to Screen and `IOPort`,
    although it was very unlikely to encounter the bug when using those
    mex files.

### Improvements and bug fixes to Screen and other drawing functions – The Visuals

-   Updates to help texts for some functions.
-   The `PsychtoolboxKernelDriver` for OS/X on IntelMacs with ATI GPU’s
    has been refined (`help PsychtoolboxKernelDriver`). Now provides
    even more precise visual onset timestamping and removes a constant
    0.4 - 0.7 msecs (depending on videomode) bias in the timestamps.
    Datapixx measurement confirms our timestamps are now spot-on on the
    two tested ATI GPU’s, a Mobility Radeon X1600 and a FireGL-V3700
-   Improvements to procedural gabor- and sinegrating rendering. Allow
    to specify a global contrast scaling factor as proposed by Xiangrui
    Li.
-   `CreateProceduralSineGrating()`: Add optional support for drawing
    procedural sine gratings with a circular aperture of selectable
    radius.
-   `PsychImaging`: Add new stereo mode `'InterleavedColumnStereo'` for
    column interleaved stereo displays, e.g., for driving auto
    stereoscopic displays based on lenticular sheet lenses or parallax
    barriers. `ImagingStereoDemo(101)` demonstrates this.

### Misc stuff

-   Some improvements to display calibration, gamma correction and color
    handling routines by David Brainard’s lab. Also improvements to the
    PR-650 photometer support.
-   Some improvements to general toolbox routines by Diederick
    Niehorster.
-   `BalanceFactors`: Speed optimization by David Fencsik.
    `BalanceTrials()` - New function for balancing a set of factors,
    contributed by David Fencsik.

Enjoy!
