---
layout: post
title: PTB BETA "Rainbows, Droids & Compute Hippies!" SP12 released
categories: news
author: kleinerm
---

The last update to the latest beta. Some feature improvements for use of the
GStreamer SDK, especially on Windows. Upgrading to the 2013.6 SDK is
recommended. Some minor other improvements and some bug fixes.

Bug fixes have been applied to the `Psychtoolbox-3.0.10` flavor as well, but
functional improvements are no longer applied to 3.0.10 aka 32-Bit OSX.

Users which want to stick to ancient OSX 10.4 or 10.5, or want to continue to
use PTB with 32-Bit Matlab on OSX are advised to switch to the
`Psychtoolbox-3.0.10` flavor immediately by use of the `DownloadPsychtoolbox()`
function with the `flavor` parameter set to `Psychtoolbox-3.0.10`. The next PTB
beta update, whenever that will happen, will remove all support for those
ancient configurations without further warning.

-   Make drawtext plugin on Linux and OSX more robust against weird fonts (non
    8bpp fonts). This fixes the bug on Gentoo Linux reported in msg \#15827.

-   Improve window focus handling for GUI windows on Linux. Don't steal window
    focus.

-   Enable video capture and recording with GStreamer SDK. Video capture works
    on OSX with the SDK. Video recording works, but so far has very low
    performance with the SDK. Functionality should work on 64-Bit Matlab on
    Windows, but is so far mostly untested.

-   Enable movie writing with GStreamer SDK 2013.6. Works ok on OSX. On
    MS-Windows, it currently manages to write a valid movie file, but often
    hangs Matlab at the end of the writing session, so this is of limited use
    on Windows...

-   Enable delay loading of GStreamer SDK dll's for 64-Bit Matlab on Windows to
    make installation of the SDK optional. `Screen()` will work without the SDK
    being installed, as long as no video capture/recording, movie writing or
    movie playback is used. This is now consistent with the behaviour on 32-Bit
    Matlab for Windows and should simplify installation of the Windows PTB a
    bit.

-   Fix regression in `BubbleDemo,` which was introduced in a previous beta
    release.

-   Allow sending arbitrary data types in `NetStation()` to the EEG system, not
    only 32-Bit integers. Contributed by Matt Mollison, University of Colorado
    Boulder, Department of Psychology and Neuroscience.

-   Performance improvements for `DaqAInScan` et al., contributed by Daniel
    Braun, University of Birmingham.

-   Fix GLU toolkit NURBS functions regression, so they can be actually used.

-   Movie demo cleanups for pure GStreamer operation and no more Quicktime.

-   Improvements to radiometric functions by David Brainard.
