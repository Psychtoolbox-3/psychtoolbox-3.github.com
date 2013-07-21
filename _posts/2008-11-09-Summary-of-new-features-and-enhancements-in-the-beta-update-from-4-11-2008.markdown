---
layout: post
title: Psychtoolbox beta update from 2008-11-4 (SVN Revision 1151)
category: news
author: kleinerm
---

This update introduces support for “formless dot field” type stimuli,
and various bug fixes and enhancements. Especially the `IOPort` driver
has been improved again.

### `IOPort` Serial port hardware support

The new `IOPort` driver has been refined in a few areas. The driver is
still much work in progress, with a few useful features missing.
However, it should be already a superior replacement for all old serial
port drivers like `PsychSerial`, `SerialComm` and Matlabs `serial`
objects for most purposes.

-   `IOPort('Write')` now supports a `blocking` flag of 2 on all
    operating systems. The old Linux specific polling for “transmitter
    empty” has been moved to `blocking` = 3. A mode of 2 now polls for
    the number of pending bytes for writeout in the system write buffer
    and repeats the polling loop until pending bytes = 0. This is
    supported on all operating systems.

-   `IOPort('Write')` now returns a couple of additional optional
    timestamps, useful for special timing calibration routines like the
    upcoming `PsychRTBox.m` driver, and for low-level debugging: A
    prewrite timestamp, a postwrite timestamp and a timestamp of last
    poll loop iteration (if used)…

-   `IOPort('Read')` accepts (for blocking reads) a new optional setting
    `PollLatency` in `IOPort('ConfigureSerialPort',...);` The setting
    allows to select the idle time between unsuccessful poll iterations,
    to trade off the system load against time quantization in such time
    critical polling loops.

-   `IOPort('ConfigureSerialPort')` allows via new options to enable
    asynchronous background reading of data from the serial port via a
    parallel background thread on `MacOSX` and GNU/Linux, this feature
    is not yet supported on Windows. If async read is enabled,
    `IOPort('Read')` will not directly fetch data from the serial port,
    but it will fetch data that has been read already in the background
    by the reader thread. This allows to automatically collect streaming
    data from serial port in the background, for later retrieval via
    ‘Read’ calls. This feature is experimental for now, its programming
    interface may change!

-   Help texts have been improved as well.

### Improvements and bug fixes to Screen and other drawing functions – The Visuals

-   `GetMouse` on OS/X fixed: If used on multi-core Macintosh computers
    with many cores, e.g., `MacPro` 8 core machines and recent
    multi-threaded Matlab versions, the function crashed Matlab reliably
    on each single invocation, unless Matlabs GUI was disabled, ie.
    Matlab was run in -nojvm mode! This was a classic race-condition,
    probably present since the very first Psychtoolbox release around
    1995! This bug only gets triggered with increasing probability on
    machines with large numbers of processor cores and on operating
    systems with efficient multi-threading support, so it basically
    never happened on single processor machines or under Mac OS 10.3 and
    earlier, and only very seldom on dual-core machines with recent Mac
    OS versions.

-   Regression in anaglyph stereo mode fixed: Anaglyph stereo as
    demonstrated in `StereoDemo` with settings 6,7,8 and 9 didn’t work.
    This is fixed.

-   Robustness improvements to `Screen('DrawText')` on OS/X: If a
    corrupt text string is supplied, the function doesn’t crash anymore,
    but abort with a (hopefully) diagnostic error message.

-   Bugfix to `Screen('DrawText')` on Windows: If text is drawn into
    different windows (onscreen or offscreen) with different text sizes
    or other different font settings, text should be drawn properly,
    instead of sometimes applying wrong settings. This was a bug in the
    way textsettings are cached internally to improve speed.

-   `Screen('FillPoly')` received a few performance optimizations.
    However most of them only had a minor impact on performance. Drawing
    of complex, concave, potentially self-intersecting filled polygons
    still needs substantial processing on the CPU and is therefore much
    slower than drawing of simple concave polygons or simple convex
    polygons (which are the fastest).

-   Potential robustness improvement for `Screen('FrameRect')` against
    broken graphics drivers when setting ‘penSize’. This is a potential
    improvement, which may or may not help on broken drivers.

-   `DrawFormattedText`: No longer aborts with error on empty text
    string as input, but simply does nothing in that case.

-   `moglmorpher`: The fast 3D morpher contained special workaround code
    for some serious bugs in the ATI display drivers on OS/X Tiger 10.4.x. 
    As i’ve learned, the drivers got fixed at least in Leopard 10.5.5, 
    so when used on 10.5, the workaround caused malfunctions on
    the fixed drivers! Now we detect the OS/X version, and only enable
    the workaround on versions lower than 10.5.5. This works now on all 10.4
    systems and 10.5.5. I don’t know how it behaves on 10.5.0 to 10.5.4, 
    due to lack of a testing system.

-   Small fix to `VideoDelayLoopMiniDemo` for use with built-in iSight
    cameras of some Macintosh computers. A bug in the OS/X operating
    system caused wrong image display on such cams.

-   Fix a bug in `PsychVideoSwitcher` driver which caused the TTL
    trigger mechanism to fail. Also extended trigger function: One can
    select if trigger should happen at each ‘Flip’ until disabled, or
    for a predetermined number of ’Flip’s then auto-disable.

-   `PsychImaging`: Add support code for setup of native 10 bpc
    framebuffers on supported ATI FireGL/Pro and NVidia GTX cards.

-   Fix in `ConvolutionKernelTest` for error handling when invalid
    convolution kernels are passed.

-   Minor other fixes and updates to help texts.

**There are still a few unresolvable serious bugs in OS/X 10.5.3,
10.5.4 and 10.5.5, especially prominent with NVidia 8000 series hardware
for which no workaround exists. E.g., multi-display operation (stereo
setups) seems to be highly unreliable and dysfunctional. Frame
sequential stereo on NVidia 8000 series hardware seems to be seriously
broken in 10.5.5. Only Apple engineering will be able to fix this.**

### New or enhanced demos

-   `FDFDemo` is a new demo: It demonstrates basic usage of the new
    `moglFDF` function, rendering an animated rotating “random dot”
    motion sphere. The `moglFDF` function allows to efficiently draw a
    special class of random dot “structure from motion” stimuli, so
    called “(F)ormless (D)ot (F)ields”. The algorithm is heavily
    inspired by the [algorithm introduced by Jedediah M. Singer and
    David L. Sheinberg in their Journal of Vision paper “A method for
    the real-time rendering of formless dot field structure-from-motion
    stimuli” (Journal of Vision, 8,
    1-8)](http://www.journalofvision.org/8/5/8/). It should behave
    mostly as the method described in that paper, but operate at a
    significantly higher speed if stimuli are demanding (e.g., high
    display resolution, large number of dots, complex underlying 3D
    geometry), as the `moglFDF` routine pushes nearly all compute
    intense operations onto the GPU, only random number generation and
    flow control are done on the CPU. However, as the paper doesn’t
    state actual benchmark numbers and i never had a look at their
    implementation, this is an unverified assumption so far. This code
    has been tested for multiple months in-house for complex 3D facial
    motion stimuli and worked well, but given its complexity there may
    remain more or less subtle bugs or limitations of the method for
    other classes of stimuli. Let me know if you find this routine
    useful and if you encounter limitations. One limitation is the need
    for half-way recent graphics hardware: Minimum requirements are a
    NVidia GeForce 6000 series card or later, or a ATI Radeon X1000
    series card or later, more specifically hardware with support for or
    later and floating point framebuffers.

-   `ImagingStereoMoviePlayer` Minor improvements.

-   `MovingLineDemo`: Changed behaviour to be more useful for exposing
    the troubles with flat panels.

-   `AdditiveBlendingForLinearSuperpositionTutorial` now also
    demonstrates how to use the TTL trigger mechanism of the
    `VideoSwitcher` device.

-   `BitsPlusCSFDemo` contrary to its name now also supports optional
    output to `VideoSwitcher` device , ATI 10 bpc framebuffer and
    `PseudoGray` output (aka bit stealing). It also allows to display an
    intensity gradient test chart instead of a CSF chart.

### Test scripts in `PsychTests`

-   Minor improvements to dualhead display sync tests in
    `GraphicsDisplaySyncAcrossDualHeadsTest` and
    `PerceptualVBLSyncTest`.

-   `KeyboardLatencyTest` now allows some assessment of the timing
    accuracy of response boxes, the response box from Cedrus, and the
    reaction time box from Xiangrui Li et al.

### Misc other stuff

-   `SearchGammaTable` and various display calibration routines improved
    by David Brainard, also improvements to `CalDemo`

-   Fix annoying warning about unrecognized escape sequence for `KbName`
    on Linux.

-   Modifications to `SerialComm` to translate a hardware path, e.g.
    /dev/cu.usbserial, to a port name and improvements to
    `FindSerialPort` by Christopher Broussard.
