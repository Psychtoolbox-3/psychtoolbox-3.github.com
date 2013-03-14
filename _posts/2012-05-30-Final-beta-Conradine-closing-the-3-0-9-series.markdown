---
layout: post
title: PTB beta release 2012-5-21 (SVN Revision 2580/2591)
category: news
author: kleinerm
---

For more details, please review the [detailed change
log](http://code.google.com/p/psychtoolbox-3/source/detail?r=2580).

This beta, nick-named “Conradine”, marks the last official Psychtoolbox
release in the Version 3.0.9 series. We may or may not fix critical bugs
after this release, but most likely we won’t.

This is the last release to support MacOSX on Apple PowerPC hardware,
the last one to support MS-Windows 2000, and the last to support Matlab
versions older than V7.4 aka R2007a

### All systems:

-   `PsychPortAudio`: Fix sound output with dithering enabled on current
    64-Bit Linux and all other future 64-Bit platforms. There was a bug
    in the underlying PortAudio library which caused strong white noise
    with dithering enabled on a 64-Bit runtime. In low latency / high
    timing precision output mode, dithering is disabled by default, so
    most demos and scripts weren’t affected. `BasicSoundOutputDemo`
    however worked in “normal mode” with dithering on by default, so the
    actual sound output was drowned in strong static white noise.

-   `Eyelink`: Fix `EyelinkFixationWindow` function for use with Matlab
    R2012a, which is case sensitive and treats wrong case in function
    names as errors, instead of warnings.

-   `PsychHID`: Add keyboard event ring buffer support. Once a keyboard
    queue for a specific keyboard(-like) device (mouse buttons on a
    mouse, joystick/gamepad buttons, etc. are treated as “mini
    keyboards”) has been created and started via `KbQueueCreate` and
    `KbQueueStart` all events (button press and release) are not only
    recorded between invocations of `KbQueueCheck`, but they are now
    additionally recorded in a ring buffer that can hold up to 10000
    press- and release events. The buffer sequentially records all
    events, including a timestamp and potential additional data. The
    buffer can be emptied (“flushed”), checked and read out with the new
    functions `KbEventFlush()`, `KbEventAvail()` and `KbEventGet()`
    independent of the old `KbQueueXXX` functions. This should allow
    more convenient access to recorded subject responses, scanner
    triggers etc. without the need to constantly poll for key state via
    `KbCheck`, `GetMouse`, `GamePad` etc. Each queue and thereby each
    individual keyboard has its own buffer (although you can only
    address one keyboard or mouse on windows due to operating system
    limitations, and only have one keyboard queue on OSX due to
    limitations of our current `PsychHID` driver, so multiple queues for
    multiple devices is only really useful on Linux). `KbQueueDemo`
    demonstrates how to use keyboard event buffers.

-   `moglmorpher`: Add more strict parameter checking to subfunction
    `moglmorpher('AddMesh')` to catch some coding errors in user scripts
    instead of aborting with puzzling error messages.

-   `Screen`: Allow to disable sound decoding of Quicktime movies during
    playback on Windows and OSX, to match behavior on Linux and Windows
    when used with the GStreamer playback engine. Precisely: Sound
    decoding is not really disabled, as Quicktime does not allow that.
    Instead sound output is just muted. This way scripts behave in a
    compatible and consistent way, irrespective of playback engine, but
    users of Quicktime won’t get the benefits of reduced processor load
    and sound resource utilization.

-   Various performance improvements in the mex files and small bug
    fixes.

-   Various improvements to color correction and gamma correction
    routines by David Brainard.

### Linux:

-   Screen: Update low-level GPU detection support to work with the
    latest year 2012 AMD GPU’s, ie., the “Southern Islands” and
    “Trinity” GPU families, better known by their marketing names
    “Radeon HD 7000” and “AMD Fusion”. This allows our special bag of
    neat low-level tricks on Linux to also work with these new models of
    graphics hardware and expose some special features not found on
    other systems.

-   `PsychHID`: Fix default keyboard selection on Linux on some Laptops,
    which report the `VideoBus` as a keyboard. If no specific keyboard
    device index is given to any of the keyboard functions, `PsychHID`
    uses a heuristic to try to select the “default keyboard” as a
    reasonable choice. As there isn’t any real “default keyboard” on any
    operating system, the heuristic is a “best effort” approach which
    can go wrong on exotic hardware setups. On Linux, some Laptops
    expose some control buttons related to graphics hardware as a “one
    button keyboard” and the heuristic sometimes chose those buttons as
    default keyboard - clearly not what one would expect. Now the
    heuristic skips those button devices labeled as `VideoBus`.
    `PsychHID` on Linux selects the default device by name pattern
    matching, selecting the first device whose name string sounds like a
    real keyboard instead of something exotic. `PsychHID` on MacOSX
    selects the first HID device labelled as “HID Usage value keyboard
    class”, so the order in which keyboards get plugged into the
    computer - or detected at boot up, or the location where they get
    connected - determines which is the default keyboard. On Windows,
    `PsychHID` can’t discriminate keyboards due to operating system
    limitations, therefore it can’t choose the “wrong one” ;-)
