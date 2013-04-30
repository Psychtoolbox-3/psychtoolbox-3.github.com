---
layout: post
title: PTB beta “Rainbows, Droids & Compute Hippies!” release 2013-04-20
category: news
author: kleinerm
---

Git tag: `PTB_Beta-2013-04-20_V3.0.10`

This release contains a couple of new features and improvements, some rather experimental by now, but also the usual amount of small improvements and bug fixes.

All systems:
------------

-   **Basic GPGPU compute support:**

    A first sketchy implementation of (G)eneral (P)urpose computation on
    (G)raphics (P)rocessing (U)nits support. We already supported (ab)use of
    GPUs for other tasks than rendering since the beginning of 2007, with our
    built-in imaging pipeline and various plugins to accelerate common image
    processing and stimulus post-processing operations. However, so far all
    functionality was implemented by reformulating computation tasks as
    graphics rendering tasks and executing them as a mixture of fixed-function
    OpenGL rendering and programmable vertex- and fragment-shading via the GLSL
    OpenGL shading language. This works very well for many visual processing
    problems, but can become awkward or inefficient for non-graphics compute
    problems. Technology progressed and nowadays most modern GPUs support GPGPU
    in a more straightforward and efficient way by use of NVidia’s CUDA API
    (for NVidia GPUs only) and OpenCL for pretty much all GPUs on the market,
    including NVidia’s, so it’s time to look into what can be done better with
    those APIs for stimulus creation. This beta release contains basic support
    for utilizing NVidia CUDA capable GPU’s under 64-Bit Matlab by use of a
    high-level open-source toolbox called “GPUmat”, which can be downloaded for
    Linux and Windows from here: [GPUmat toolbox download link](http://sourceforge.net/projects/gpumat)

    GPUmat allows to implement computational methods in familiar Matlab language,
    as it extends Matlab with new GPU data types GPUsingle and GPUdouble. If
    vectors and arrays are created with this datatype, then the data is stored on
    the GPU and processed in parallel by the GPU. Psychtoolbox initial
    implementation provides builtin functionality to detect if GPUmat is installed
    and to initialize it, if so. It also provides an interface for efficient data
    transfer and synchronization between GPUmat and Screen/OpenGL. Screen’s
    floating point framebuffers, offscreen windows and textures can be efficiently
    passed to GPUmat as GPUsingle matrices to do computations on them and resulting
    matrices can be converted back into PTB’s representation for post-processing,
    rendering and display. In this initial release, I focused on getting the
    high-level setup code right to hopefully allow future painless extensions, and
    to optimize data transfer between PTB/OpenGL and GPUmat/CUDA.

    Benchmarking showed that the current data transfer works with \> 90% of the
    theoretical peak performance of the tested GPU under Linux, with about 30-40%
    efficiency on Windows, and IIRC in the 1-2% range on OS X. Profiling showed that
    the OS X implementation essentially performs data exchange with the speed of a
    slow software fall-back path and unsurprisingly the deficiency seems to be in
    the OS X graphics subsystem - another area where the most advanced operating
    system in the world falls way short of its competitors. This means that if you
    like to use this functionality, you can gain an almost 100x performance boost
    for some tasks by running you Mac under Linux instead of OS X.

    There are currently three demos in the `PsychDemos/GPGPUDemos` subfolder, all
    showing fast application of a 2D-FFT and inverse FFT to GPU accelerated image
    filtering by replacing convolution with a point-wise multiply in frequency
    space.

    Current restrictions: Only 64-Bit Matlab supported, as GPUmat needs object
    oriented programming support v2 (“`classdef`” OOP) which is not yet available in
    stable releases of GNU/Octave. However, octave’s `classdef` support has made
    quite a bit of progress, so I’m optimistic this will work for stable octave in
    the not too far future. Only 64-Bit because I’m too lazy to maintain this for
    32-Bit as well. There are not technical reasons, just that people should move
    to 64-Bit if they want to do this style of computing efficiently. Only NVidia
    CUDA capable GPU’s for now, as GPUmat is based on CUDA. The long-term goal
    would be to primarily support OpenCL, as it is cross-platform, cross-vendor and
    also supports non-GPU compute accelerators. Only Linux and Windows as of today,
    because GPUmat is not yet available for OS X. I ported it to 64-Bit OS X, but
    haven’t submitted it upstream for inclusion into the official distro yet,
    that’s a todo.

    Setup instructions under `help PsychGPGPU`, demos under `help GPGPUDemos`.

-   `RenderDemo` shows a new way to use our imaging pipeline and new plugins to
    perform GPU accelerated color space conversion and calibration. New
    functions of the imaging pipeline allow to convert from the XYZ tristimulus
    color space to calibrated RGB output, taking the calibration data from our
    color calibration routines into account.

    [Wikipedia's definition of XYZ color space](http://en.wikipedia.org/wiki/CIE_1931_color_space)

    The advantage is that all the color calibration can now get easily integrated
    into our stimulus post processing pipeline, and of course speed. The demo also
    shows a new plugin to convert from xyY color space to XYZ color space. It should
    be noted that this is only lightly tested. While light testing of a few sample
    values showed proper behaviour, David Brainard wants to write more exhaustive
    unit tests at some point in the future. Of course patches for tests are
    welcome.

-   CRS Bits\# support: The display subsystem of the Cambridge Research Systems
    Bits\# device is now fully integrated for convenient and efficient use. The
    I/O system is todo. Demos and tests have been updated to take advantage of
    new Bits\# functionality like improved diagnostic and troubleshooting.

-   PR-705 photometer support contributed by Zachary Lindbloom-Brown.

-   The ColorCal2 driver now also works with GNU/Octave, thanks to the donation
    of a ColorCal-II by CRS. The driver seems to work very well on Linux, is a
    hit and miss on OS X, apparently due to funny new OS X bugs or
    incompatibilities, and was a no-go for me so far on Windows. The current
    driver uses USB-HID protocol to communicate with the device, which seems to
    be flaky on non-Linux. It might make sense to switch it over to good old
    Serial-over-USB protocol which is probably more trouble-free on the other
    OS’es.

-   OptiCal support, contributed by Andreas Widmann, although it could be this

-   Various smaller fixes and improvements, e.g., updates to demos,
    `DrawFormattedText` now accepts arbitrary ’rect’angles for layout of text,
    not only the bounding rectangle of the target window or texture, OS
    specific fixes, …

Linux:
------

-   Linux Google Nexus-7 / ARM support:

    Included in this release is experimental support for the Google Nexus-7 tablet
    when run under Ubuntu Linux 13.04 “Raring Ringtail”, 32-Bit ARM edition. This
    won’t work under the normal Android OS on the tablet, but you will need a
    tablet edition of Ubuntu desktop Linux, either as only operating system, or as
    dual-boot setup in parallel to your Android OS. Psychtoolbox seems to work
    reasonably well on the tablet, with a certain amount of tweaking.

    What works? `GetSecs`/`WaitSecs` with usual precision, real time scheduling, sound
    (PsychPortAudio and 3D OpenAL), keyboard and mouse I/O — touch input as mouse
    input, IOPort and PsychHID stuff is so far untested, but expected to work
    normally if you have an OTG adapter cable, `Screen()` and MOGL 3D OpenGL mostly
    works, i.e., all the basics work. What doesn’t work is functionality that
    requires programmable shading support, as we currently only support
    OpenGL-ES1.1 fixed function rendering, not OpenGL-ES2.0 programmable shading.

    [Simple installation instructions for Ubuntu Linux on the Nexus-7 under this link.](https://wiki.ubuntu.com/Nexus7)

    This would wipe your Android OS and data from your device, so no more “Cut the
    rope” or “Angry Birds” for you, but all the fun of drifting gabor patches and
    movie playback.

    I chose a dual-boot setup, which preserves Android and its goodness, but
    requires serious tinkering, and averaging installation instructions over
    multiple partially incomplete or mutually contradictory howtos, e.g.,
    [this howto.](http://forum.xda-developers.com/showthread.php?t=2011403)

    Anyway, this is mostly a test setup for now to see how much interest there is
    in Psychtoolbox for mobile devices and what the challenges are. I chose the
    Nexus-7 because it is the reference device for porting and testing Ubuntu Linux
    and it is also rather good price/performance at 200\$/Euros.

-   Linux highly experimental multiple display and rendering backend support:
    Not really interesting for now, but this is to test next generation display
    system support for the Linux PTB, ie., non-X11 display setups, EGL,
    Wayland, raw framebuffer, Android and OpenGL-ES / OpenGL-3/4/…

OS X:
-----

-   More fixes for OS X Retina and LCD timestamping brokeness and other OS X
    bugs. I now recommend to always install the `PsychtoolboxKernelDriver` if you
    use OS X 10.7 or later and want precise stimulus onset timing or
    timestamping. The level of OS X brokenness has reached the point where our
    own implementation is almost always better than what Apples OS has to
    offer. E.g., OS X beamposition queries are only supported anymore on NVidia
    GPU’s and scheduled by Apple for complete removal in a future OS X release.
    Even on NVidia the mechanism is slightly broken and inaccurate on all
    modern GPUs and totally broken as of OS X 10.8 for any kind of digital flat
    panel / LCD / DVI-D etc. - it only sort of works for classic analog VGA
    connected CRT monitors.

