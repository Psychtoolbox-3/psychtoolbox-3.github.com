---
layout: post
title: PTB beta “Death by a thousand paper cuts” release 2012-10-09
category: news
author: kleinerm
---

[Psychtoolbox-3/Psychtoolbox-3@759f023b][commit] at [GitHub](https://github.com/Psychtoolbox-3/Psychtoolbox-3)
tag: `PTB_Beta-3.0.10.20121009`

This is mostly a bug-fix release to deal with various operating system and
graphics driver bugs discovered after the last release.

Release Highlights:
-------------------

All systems:
------------

*  The Speak() command is now supported on all operating systems, and made more
   flexible. Very flexible Linux support via speech dispatcher service added.
   Basic MS-Windows support added by Vishal Shah from the Pelli lab at NYU. Mac
   OS support made slightly more flexible.

*  Improvements to general graphics driver sync tests to catch some interesting
   potential future bugs. Some warning clutter removed where it was redundant.

*  Enhancements to the PsychPortAudio backed `Snd()` legacy sound command: `Snd()`
   uses PsychPortAudio internally for higher robustness. However, this means
   that use of `Snd()` is incompatible with simultaneous use of `PsychPortAudio()`
   within the same script. `Snd()` now notifies you of this, and also falls back
   to the old Matlab / Octave `sound()` function, if PsychPortAudio is already in
   use.

*  Some improvements to DKL color functions by David Brainard.

*  Make Screen startup more artifact free on setups with `OpenGL`
   triple-buffering enabled. So far you have to disable triple-buffering on any
   graphics driver on any operating system to get PTB to work correctly
   timing-wise. Or more specifically, you have to refrain from enabling
   triple-buffering, as triple-buffering is off on almost all graphics drivers
   and operating systems by default. However, i've just submitted patches with
   improvements to the Intel and Nouveau drivers for Linux. Once the improved
   drivers will be released, you will be able to use the drivers with
   triple-buffering enabled on Intel and `NVidia` graphics cards , and then it
   will be nice to have a good looking, artifact free start screen.

*  Fix for NVidia graphics driver bug on all platforms, which caused output of
   many errors when using `GL_TEXTURE_2D` textures in some demos, e.g.,
   `BlurredMipMapDemo`.

Windows:
--------

*  Fix `pnet()` data reception on 64-Bit Matlab. Certain parameters for data
   reception could cause it to crash due to a 64-Bit compatibility bug.

*  Fix `ShowCursor()` and `HideCursor()` on some MS-Windows setups.
   `HideCursor()` wasn't hiding the cursor anymore on some setups for no
   conceivable reasons, whereas it worked flawlessly on others, without any
   change of code on our side.

Linux:
------

*  Improved correctness tests and wokarounds for a graphics driver bug on Intel
   graphics cards under Linux. A bug was introduced into the Intel drivers
   released after July 2011, which slipped through (my) code review. This could
   cause too early stimulus onset, earlier than requested via the `when`
   parameter of `Screen('Flip')` - basically the parameter was ignored and flip
   always happened at start of the next video refresh cycle. Psychtoolbox
   automatic correctness tests didn't test for this, so it slipped through
   ptb's tests as well :-(. However, the problem was easily detectable by
   checking the timestamps returned by `Screen('Flip')`, or in the case of long
   interstimulus intervals or animations by visual inspection. Psychtoolbox now
   checks for this type of bugs as well, warns the user and switches to a
   fallback path to workaround the problem until a graphics driver update fixes
   the bug for good. A bugfix for the graphics driver has been submitted for
   inclusion into future Intel graphics driver releases.

*  Make Linux `Screen()` compatible to apitrace utility. apitrace is a tracer
   for OpenGL applications. Very useful for debugging bugs in OpenGL code.
   Calling `setenv('PSYCH_ALLOW_APITRACE', '1')` makes it possible to trace
   Psychtoolbox execution of OpenGL commands for debugging of hairy bugs in
   OpenGL code.

*  Bugfixes and enhancements to `Screen('Resolution')` on Linux. It could
   return stale information after a display resolution switch in some cases.

OSX:
----

*  Bugfix for Screen('Resolutions') on 64-Bit OSX. It crashed 64-Bit
   Matlab/Octave on OSX when called.

*  Catch errors during HID device enumeration and handle them more gracefully
   by output of a useful error message instead of crashing hard later. This to
   work around bugs in Apple's 64-Bit HID Utilities framework (shoddy error
   handling), and potentially in some OSX HID drivers, e.g., for certain Wacom
   tablets. A specific tablet model could crash PsychHID by messing with device
   enumeration, as reported in Issue#62 on Psychtoolbox-3 at GitHub.


[commit]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/commit/759f023b86fb3632b2a7e3959d60e32c6b9df7e5
