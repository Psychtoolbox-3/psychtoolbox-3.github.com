---
layout: post
title: Stop! PTB BETA RELEASE "Hammertime!" 
categories: news
author: kleinerm
---

Stop! It's time for Hammertime :)

Hammertime contains mostly bug fixes, but also a few neat improvements: Break
it down!

Change of software requirements:

-   Go with the flow! Psychtoolbox for 32-Bit Matlab on MS-Windows now uses and
    *requires* the GStreamer SDK, instead of the rather old GStreamer runtime
    from the OSSBuilds project. If you want to use multi-media functions, you
    will need to uninstall your old OSSBuilds GStreamer and install the 32-Bit
    GStreamer SDK. `help GStreamer` contains updated instructions.

If you want to stick to the old SDK, you can `DownloadPsychtoolbox()` with
flavor `Psychtoolbox-3.0.11-PreWinGStreamerSDK`. This will download and lock
your Psychtoolbox permanently to the "Stadtmusikanten" release from last week,
the last PTB to support OSSBuilds GStreamer.

Bug fixes: Just for a minute let's all do the bump, bump, bump

-   Bugfix for GStreamer OpenGL bugs on Windows for movie playback with special
    `pixelformat >= 6`. Thanks to Matthew Edmundson for help in debugging this.

-   Bugfix for Linux + PsychHID: A bug in HIDAPI, the FOSS library we use as
    backend for low-level USB-HID device access, caused the failures described
    by Ian Mackenzie in forum message \#16555. After use of a PsychHID
    low-level function, Octave and Matlab stopped parsing decimal numbers iff
    the system number formatting ("Country and language settings") was setup to
    use "," instead of "." as a decimal point. E.g., german number formatting
    would do this. An update of PsychHID to a bug fixed HIDAPI solved this.

-   Bugfix for OSX crash at window close due to Apple OSX CVDisplayLink bugs on
    Matlab R2013b, as reported by Keith Schneider in forum msg \#16553.
    Hopefully...

Improvements and new functions: Fresh new kicks advance!

-   OpenGL context sharing support between "windowed" non-fullscreen windows
    and fullscreen windows on OSX is now sometimes possible, at least on OSX
    10.7 and later with NVidia cards, maybe also with other cards or an earlier
    OSX version. This means that the scenario desired in forum message \#16114
    may now work at least on some OSX setups. This enhancement was possible
    because we dropped support for OSX 10.5 and i could cleanup and rewrite our
    window and OpenGL context setup code to take advantage of some post-10.5
    features.

-   Improved GUI window support. GUI windows now click better with some users.

-   Low-level support for latest and upcoming AMD GPU's on Linux and with OSX
    `PsychtoolboxKernelDriver`. Beamposition timestamping and other special
    goodies should work with those new gpus.

-   You can't touch this! WinTabMex for touch screens and digitizer tablets
    with WinTab api is now also available for 64-Bit Matlab on Windows, thanks
    to some enhancements contributed by Jason Friedman.

-   At the end of the day, stop a bit for some hammertime in `PlayMoviesDemo`'s
    cool video section, and bust a few moves.
