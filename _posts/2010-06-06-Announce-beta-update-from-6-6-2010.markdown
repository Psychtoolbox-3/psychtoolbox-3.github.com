---
layout: post
title: PTB beta released 6.6.2010 (SVN Revision 1737)
categories: news
author: kleinerm
---

This summarizes all new beta features from 11.1.2010 up to 6.6.2010.
[The list of improvements is likely incomplete as always. For detailed
logs, click this
link](http://svn.berlios.de/wsvn/osxptb/beta/?op=log&rev=0&sc=0&isdir=1).

Some users of Microsoft Windows may encounter an error during update or
download of the toolbox. On failure, the installer will give you
instructions on how to download and install updated copies of the
Microsoft Visual C runtime libraries to make Psychtoolbox work again.
This is a required upgrade, forced by some changes in Microsofts OS.

These updates introduce various bug fixes and enhancements. Especially
the `Screen` and `PsychPortAudio` and `Datapixx` drivers as well as the
image processing pipeline and many demos and drawing functions have been
improved again.

### `PsychPortAudio` sound driver

-   Bugfix for audio artifacts due to “wraparound errors” in the
    Portaudio sample converters. Could cause audio artifacts if sound
    samples reached the (legal) signal level 1.0 and the soundcard
    expected audio data converted to 24 bit integer or 32 bit integer
    format. This mostly affected some ASIO soundcards on Windows.
-   Perform clamping of audio output signals to valid -1.0 to +1.0 range
    in all modes by default, instead of only in non-low-latency mode as
    in previous versions of the driver. Allow to change defaults for
    dithering and clamping in the ‘Open’ function.
-   On Windows with some ASIO soundcards and on Mac OS with some
    external soundcards, direct input monitoring is supported. This
    requires hardware support by the soundcard and allows to feed back
    sound from the soundcards inputs (microphone etc.) to its outputs
    with minimal latency. Most soundcards don’t support this feature, so
    you’ll need to use `PsychPortAudio's` software implementation which
    has a slightly higher latency.
-   Improved support for sound schedules: Now allows to specify and
    schedule onset/offset/pauses of sounds wrt. to the system clock,
    i.e., in the same timebase as `GetSecs` and all other timestamps in
    Psychtoolbox.
-   Support for virtual audio devices and mixing: Allows to open a
    physical soundcard as a master device, then create multiple “slave
    devices” which attach to different channels of the master device.
    Output of multiple slave devices is combined/merged/mixed and send
    to the master device. This allows to play back multiple independent
    soundtracks simultaneously and with independent control of content,
    timing and volume. Also allows to address each channel or set of
    channels on a card separately. New function
    `PsychPortAudio('OpenSlave')` controls this functionality.
-   Support for capturing and recording the mixed output stream as it
    gets sent to the real soundcard, e.g., for feedback, testing,
    debugging and documentation purpose.
-   Support for per device and per channel gain and volume control via
    the new ‘Volume’ function.
-   Support for precisely timed amplitude modulation (AM) of each
    virtual audio output slave device by definition of time series of
    gain values which can be applied with sample-accurate timing. Cfe.
    `BasicAMAndMixScheduleDemo` for demo of AM modulation, volume
    control, mixing and scheduling support.
-   Option to resume playback in a ‘Start’ call where it was last
    ’Stop’ped, instead of restarting at the beginning.

### Serial port hardware support

-   Some performance improvements to `IOPort` and some parameters to
    allow to workaround operating system / serial port driver bugs on
    some setups.
-   `CMUBox` driver for serialport or USB response boxes now supports
    also the `fORP` device when connected via a serial port and to use
    the `UBW32/Bitwhacker` as a response button box.

### Improvements and bug fixes to Screen and other drawing functions – The Visuals

-   Further improvements to high precision visual stimulus onset timing
    and timestamping. Also added new tests and workarounds for various
    broken graphics drivers on Windows and Mac OS.
-   Experimental support for `OpenML` based visual stimulus onset
    scheduling and timestamping for GNU/Linux. This is an opt-in, work
    in progress. Not yet ready for mainstream use, but will allow to
    take advantage of Linux special facilities, once they are completed
    and stable.
-   Support for NV\_swap\_group and SGIXX\_swap\_group extensions on
    Linux and Windows. Some professional grade graphics cards, e.g.,
    some AMD `FireGL/FirePro` cards and some cards do support these
    extensions in hardware. These allow to perfectly synchronize
    bufferswaps and visual stimulus timing across multiple windows,
    displays, graphics cards or even different nodes on visualization
    clusters. `Screen` will automatically use these extensions if they
    are present and a dual-display stereo mode or other dual display /
    multi window mode is used.
-   Support for creation and writing of Quicktime movie files on Mac OS
    and Windows. Allows to create and write movie files. Currently only
    supports one video track per movie and doesn’t support soundtrack.
    Works with any codec supported by Quicktime. `ImagingStereoDemo`
    contains test- and example code to demonstrate usage. Can create a
    movie which records the animated stereo display.
-   Various bugfixes and help text updates.
-   The imaging pipeline `PsychImaging` in conjunction with
    `PsychColorCorrection` now also allows to apply automatic display
    vignetting correction aka shading correction to automatically
    compensate for spatially varying differences in luminance or per
    color gains of display devices, e.g., due to lense vignetting on
    projectors. `VignetCalibration` implements an interactive
    calibration procedure, `VignettingCorrectionDemo` and
    `AdditiveBlendingForLinearSuperpositionTutorial` demonstrate how a
    calibration is applied for realtime vignetting correction.
-   `ScreenDrawDots` is a reimplementation for the `Screen('DrawDots')`
    function to allow smooth dot drawing on broken Mac OS 10.6.3
    systems.
-   `PsychDrawSprites2D` allow for drawing of large numbers of similar
    textures, so called Sprites. It behaves exactly like
    `Screen('DrawDots')`, except that it doesn’t draw dots, but little
    copies of a given texture, with selectable size, position, rotation
    and color. This is demonstrated in `DotDemo` by passing an optional
    flag.
-   A new `Sadowski-Illusion` demo.
-   Full support for the VPixx technologies DataPixx device on all
    platforms, except Apple `PowerPC` and Windows with Matlab versions
    before V7.4 (R2007a). All special graphics display functions
    (stereo, multi-display, mirroring, high precision color and
    luminance display) are supported via `PsychImaging`, e.g.,
    demonstrated in `BitsPlusCSFDemo`,
    `AdditiveBlendingForLinearSuperpositionTutorial` and
    `ImagingStereoDemo`. Timestamping functionality and other
    convenience functions, as well as audio capture and voice keys are
    available via `PsychDataPixx` and `DatapixxAudioKey`,
    `PsychPortAudioDatapixxTimingTest`. See
    `help DatapixxToolbox`. All low-level features are supported via
    the`Datapixx` mex file driver.
-   OpenGL for Matlab and Octave: Add support for GLU tesselator
    functions.
-   New `DotRotDemo` for rotating dot fields by Keith Schneider.

### Misc stuff

-   Many new and improved display calibration, gamma correction and
    color handling routines by David Brainard’s lab.
-   Some improvements to general toolbox routines by Diederick
    Niehorster.
-   Support for later models of the `RTBox` response button box in the
    `PsychRTBox` driver.
-   Bugfixes and workarounds for the latest collection of bugs in Mac
    OS/X Snow Leopard 10.6.3 and MS-Windows.
-   Compatibility fixes to mex files to provide good support for Ubuntu
    Linux 10.04 LTS “Lucid Lynx”.

Enjoy!
