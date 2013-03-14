---
layout: post
title: Psychtoolbox beta update from 2008-06-09 (SVN Revision 1064)
category: news
author: kleinerm
---

This update, apart from the usual bug fixes (mostly for broken graphics
card drivers, but also for a few ptb bugs) mainly improves support for
high precision drawing and display of visual stimuli. Another major part
is consistent support of serial port access for all operating systems
and runtime environments. And then there are lots of improvements to
single functions.

### Hardware support

-   Experimental support for the basic functions of the USB 1024-LS
    digital `I/O` box on Apple OS/X. This is implemented but untested –
    no feedback was received by any of the persons who wanted to try it.

-   Support for [Cedrus response boxes of the RBx30 series and
    compatible XiD
    devices](http://www.cedrus.com/responsepads/rb_series.htm). See
    “help CedrusResponseBox” for how to use the new CedrusResponseBox
    command to operate and query the box. Please note that the current
    driver only “sort of works” for the basic features of the box,
    although a lot of time has been spent by multiple people trying to
    make it work. More advanced features are implemented, but their
    reliability is low enough to render them useless for most purpose.
    Basic key queries and button event queries work, so you can actually
    get responses from your subjects. Queries of the built-in timers
    work, but due to some interesting design flaws in the protocol, i’m
    not sure what they should be good for, unless you can get external
    baseline signals from the TTL trigger input ports. Setup, control
    and query of the TTL i/o port sometimes (in about one third of all
    trials) works under some random and unrepeatable circumstances, so
    good luck if you want to use them. I am still waiting since 30th of
    April for any helpful comments or suggestions from Cedrus developer
    support about how one can make their devices more cooperative with
    software other than their own. Thanks to Jenny Read, Cambridge
    Research Systems, Jon Peirce, Thomas Tanner and Tobias Wolf for
    suggestions, code examples, testing or sharing the pain.

-   Improved support for the EGI/Netstation EEG system. Our old
    NetStation control function apparently only worked on PowerPC based
    Macintosh computers. The new driver works on all Apple Macintosh
    computers and should also work on Intel PC under Windows and Linux.
    Thanks to Gergely Csibra and Zhao Fan for fixing this.

-   The pnet mex file for TCP/UDP/IP support has been recompiled to
    allow for lower communication latency. This should improve timing
    for at least NetStation and the iViewX eyetrackers.

-   Serial port support: This update contains the first release of
    “IOPort”, a new cross-platform driver for control of Input/Output
    ports. The driver works with Matlab and Octave on all supported
    operating systems OSX, Linux and Windows. This initial release
    provides unified support for serial ports, both native ones and
    serial ports emulated over USB protocol or other protocols. Future
    versions of the driver are intended to provide support for other
    types of I/O ports, e.g., parallel ports. As of now, the driver is
    only used by the CedrusResponseBox M-File, but long-term all code
    should be switched to this unified driver, e.g., the PR-650
    photometer routines etc, so we can get rid of special solutions like
    PsychSerial or SerialComm.

-   Mouse wheel support: On OS/X the function GetMouseWheel() allows
    query of the state/movement of the mouse wheels of wheel mice.
    However, this seems to occassionally crash after multiple “clear
    all” -\> run script -\> “clear all” cycles for yet unresolved
    reasons.

### Improvements to Screen – The Visuals

Most improvements are related to the image processing pipeline. While
the detailed documentation is contained in the files referenced below,
most functions are accessed and controlled by the `PsychImaging`
function and the basic help for how to use them can be found there.
Demos mentioned below demonstrate this stuff in “real world” scripts.

-   Much improved HDR/High precision drawing support, including improved
    GPU capabilities detection, especially on Apple OSX: Psychtoolbox
    should support drawing of arbitrary color values, even ones with
    negative signs, on OS X as well. In the past, this feature was only
    available on MS-Windows and Linux due to some software design
    restriction in all versions of OS X. PTB can now detect such
    restrictions and enable a special internal workaround solution that
    achieves the same without relying on the operating systems support.
    The ability to draw “negative” color values is mostly useful for
    subtracting color from a given framebuffer image in combination with
    alpha-blending, e.g., for fast and efficient drawing of large
    numbers of gabor patches or superimposed patches. Examples of this
    technique are demonstrated in
    `BitsPlusPlusAdditiveBlendingForLinearSuperpositionTutorial` or
    `GarboriumDemo`. There is also a new but not fully finished test
    script `HighColorPrecisionDrawingTest`. It allows to get some basic
    measures of the accuracy (how closely does the drawn color/luminance
    match the requested one) of drawing commands. Some test cases
    sometimes give worse numbers than they should due to some quirks in
    some graphics cards which are unrelated to accuracy but confounded
    with it. E.g., if the majority of test results tells you that your
    system can draw with 16 bits of precision, but one or two tests tell
    you it only has 6 bits or 0 bits of precision, then you can assume
    that the 16 bits is the more correct number and the other one is the
    outlier.
-   This functionality is mostly controlled by the special
    `floatprecision` flags of `Screen('MakeTexture',...)` for drawing of
    high precision textures, and the `Screen('ColorRange',....)` command
    for drawing of other primitives and control over the required
    precision, value range and clamping behaviour of such drawing
    operations. General control of framebuffer precision is again done
    via `PsychImaging` and its subfunctions.

-   High precision display device drivers for most common devices, and a
    test to test them:
  -   [CRS Bits++ in all
      modes](http://www.crsltd.com/catalog/bits%2B%2B/index.html) – Detail
      improvements: Support for automatic gamma correction in Mono++ and
      Color++ modes (see below) and for overlay windows in `Mono++` mode.
      Some automatic fixes for some broken graphics drivers as well.
  -   [VideoSwitcher by Xiangru Li et
      al.](http://lobes.usc.edu/VideoSwitcher/) – A video attenuator
      device with active amplifiers, useable with standard RGB monitors
      for high precision luminance output, including a single TTL trigger
      output port. See help for `PsychVideoSwitcher`.
  -   Generic video attenuator support via Lookup table transforms: Allows
      to drive any attenuator style device. You create some Luminance to
      RGB lookup table for your device in a device specific manner. Our
      driver performs automatic mapping of luminance values to proper RGB
      values from the table. Supports devices with up to 16 bit luminance
      resolution.
  -   [PseudoGray shader aka
      BitStealing](http://r0k.us/graphics/pseudoGrey.html): An algorithm
      that tries to squeeze out a few extra bits of luminance reproduction
      on standard 8 bits per color component graphics cards: See help for
      `CreatePseudoGrayLUT`
  -   ATI 10 bpc framebuffer refinements: See help for
      `PsychHelperCreateARGB2101010RemapCLUT` and for
      `PsychtoolboxKernelDriver`
  -   `BrightSideHDR` refined: Support for the [DR37-P high dynamic range
      display](http://en.wikipedia.org/wiki/DR37-P) from `BrightSide` also
      received a few detail improvements.

The `BitsPlusPlusAdditiveBlendingForLinearSuperpositionTutorial`
currently demonstrates how to enable and use the different drivers in
its source code. While this script used to only demonstrate mode, it its
now more generic and will need a new name. The
`HighPrecisionLuminanceOutputDriversImagingPipelineTest` tests accuracy
of the different output drivers, except for the CRS `Bits++` which has
its own test script like in the past.

-   Color management integrated into all opmodes, e.g., gamma
    correction: This applies only in conjunction with use of the imaging
    pipeline. It should work with all HDR / high precision output
    drivers (see above). Read help for `PsychColorCorrection` for an
    overview. Currently only a simple gamma correction is implemented,
    but this is easily extensible.

-   High quality spatial display calibration and geometric undistortion
    routines, [contributed by the Banks Vision Lab at University of
    California, Berkeley](http://bankslab.berkeley.edu/). Read  `help DisplayUndistortionBVL`
    for an overview of functionality and usage of the calibration
    procedure. Their website also contains some instructions. The
    current help text was mostly written by me, so i’m the one to blame
    for sloppy explanations and they are the ones to praise for high
    quality calibration routines ;-)

-   Some new PsychImaging subfunctions, e.g., dynamic selection of
    processing ROI: You can restrict image processing to some subregion
    of the display to save computation time if you need high redraw
    rates on high resolution displays, your graphics card is too slow
    and the stimulus only covers a fraction of the display area.
