---
layout: post
title: PTB BETA RELEASE "Blue skies and empty brains" - SP2
categories: news
author: kleinerm
---

Mostly bug fixes and minor improvements, most interesting is probably the
`Eyelink()` stuff.

-   Fix download failure for legacy v3.0.10 in `DownloadPsychtoolbox()` on
    32-Bit Matlab for OSX.

-   Fix mex file load errors on 64-Bit Octave for OSX with Octave installed via
    Fink package manager and for other versions of Octave than 3.6.1 with
    HomeBrew.

-   New function `Eyelink('SetAddress')` for setting tracker computer target IP
    address, to allow selection of non-default IP address.

-   Enable raw sample data access for Eyelink on Linux. This requires the
    latest Eyelink packages for Linux, Windows, OSX. For entertainment value,
    SR-Research provides up to date 32-Bit packages for Debian/Ubuntu Linux via
    automatic software update, but delivers outdated and incompatible 64-Bit
    packages via software update, despite matching version numbers and release
    dates! However, downloading and manually installing the `.tar` archive for
    64-Bit from their Linux support area works fine. Great release engineering
    guys, i had so much fun with this!

-   Updated help for `PsychVideoSwitcher` by Xiangrui Li to clarify how the
    toggle between Luminance and RGB mode works.

-   Update some other help texts, e.g., `DisplayOutputMappings,` to describe
    multi GPU support/issues/workarounds.

-   Add new text rendering mode 0 on OSX for new-style ATSU rendering of
    problematic exotic fonts. `Screen('Preference', 'TextRenderer', mode)` still
    defaults to 1 on OSX, but a setting of 0 uses a different layout strategy
    which handles some fonts better, e.g., Denis Pelli's "Kuenstler LT", while
    breaking layout for other fonts, e.g., Japanese Kanji. Great work Apple,
    you rule! The best solution is actually to use mode 2, which uses the
    (ported) Linux text renderer instead of the Apple text renderer on OSX.
    That renderer handles all known fonts at same or better quality and
    flexibility with much higher performance. However, we stick to classic mode
    1 on OSX for reason of consistency, so modes 0 and 2 are opt-in.

-   Add GstX264Enc video encoding profile for fast `camerabin2` video recording
    with GStreamer SDK. This makes VideoRecording work reasonably well with the
    GStreamer-SDK on 64-Bit Windows.

-   Some new demos and improvements from David Brainard in area of color
    calibration or simulation, e.g., `IsomerizationInDishDemo.`

-   New function GetGITPath from Ben Heasley.
