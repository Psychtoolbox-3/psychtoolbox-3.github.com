---
layout: post
title: PTB beta “Broken Windows” release 2012-09-15
categories: news
author: kleinerm
---

[Psychtoolbox-3/Psychtoolbox-3@fde2c3f5][commit] at [GitHub](https://github.com/Psychtoolbox-3/Psychtoolbox-3)

Most importantly this release adds 64-Bit Matlab support for MS-Windows and
removes Octave support and Quicktime support for MS-Windows.

Release Highlights:
-------------------

Windows:
--------

*  The runtime library requirements have changed: Now our mex files require the
   MSVC-2010 runtime libraries. Installers for these are contained in the
   `Psychtoolbox/PsychContributed` folders (`vcredist.exe`, `vcredist_x64.exe`).

*  The prehistoric `PsychSerial()` command has been removed. Use `IOPort`
   for serial i/o.

*  GNU/Octave support for MS-Windows completely removed. After over 3 years of
   availability on Windows, only about 117 of over 22000 MS-Windows users gave
   Octave a try - that's only 0.5%, so i consider this a failure and declare
   defeat. If you want to continue using Octave 3.2.4 with Psychtoolbox on
   Windows, you must refrain from updating PTB 3.0.10 any further, or stick to
   PTB 3.0.9, otherwise the update will delete your Octave mex files.
   `DownloadLegacyPsychtoolbox()` always allows to downgrade to the
   unsupported v3.0.9 and then stick to that.

*  Apple Quicktime support for Windows finally completely removed. Now
   GStreamer is mandatory for multi-media functionality on Windows (Movie
   playback, movie creation, video capture, video recording). `help GStreamer`
   will tell you how to install it.

*  64-Bit Matlab support for MS-Windows added. Limitations: At the moment, on
   64-Bit Matlab, GStreamer must be installed for `Screen()` to work at all, even
   if you don't use any multi-media functions. `Eyelink()` is unsupported with
   64-Bit Matlab, as SR-Research doesn't support 64-Bit Windows yet afaict.
   Datapixx support is missing, but will probably get added soon.

*  A new `PsychTweak()` command allows to control some parameters on how
   clocks are handled on MS-Windows. This allows to change the way broken clock
   hardware on MS-Windows is detected and handled. The defaults have been
   changed to be a bit more lenient to tolerate some brokeness in the latest
   processors on Windows.

OSX:
----

*  32-Bit Octave support on OSX removed, 64-Bit Octave 3.6 support added.
   Should work with Octave installed via the "HomeBrew" package manager.

*  Optional `GStreamer` support for 32-Bit Matlab on OSX added. Now you can
   use it on 10.6 Snow Leopard and later. Apple Quicktime is still the default
   on 32-Bit Matlab for OSX, the `Screen('Preference')` switches allow you to use
   `GStreamer` instead.

*  The `PsychtoolboxKernelDriver` on OSX now supports Intel integrated
   graphics cards as well.

I consider the 32-Bit PTB for OSX now on “live support”. I have one machine
left for maintaining it. As long as that machine keeps working and is not
getting upgraded to 64-Bit, i'll keep the 32-Bit PTB for OSX alive.

Linux:
------

*  Windowed window support and GUI window support now shows same level of
   functionality and behaviour as on OSX, e.g.,
   `PsychDebugWindowConfiguration` is now fully useable.

All systems:
------------

*  Movie playback performance and functionality improvements for `GStreamer`
   based movie playback engine. Some perf. improvements for videocapture
   engine, and basic `GeniCam/GigE` video capture support. The default
   behaviour and performance is the same, but some optional switches now allow
   to enable multi-threaded video decoding for some codecs, e.g., H264 and use
   of optimized texture upload methods for some movie formats. This can speed
   up playback of high framerate and high resolution videos considerably on
   high end machines with many cores and modern gpus. `PlayMoviesDemo()` has
   some new optional parameters `pixelFormat` and `maxThreads` which allow to
   enable these optimizations, e.g., on H264 video. E.g., a pixelFormat = 6 and
   maxThreads = 0 will use as many processor cores as available for video
   decoding. On Linux and OSX this can provide over six-fold speedup, on
   Windows the multi-threading seems to be mostly ineffective at the moment,
   probably due to some codec bugs on Windows.

*  Support for `GL_TEXTURE_2D` textures as render targets (e.g., Offscreen
   windows and use with `TransformTexture`) -- For improved OpenGL interop with
   3rd party OpenGL code like Horde3D. Non-power-of-two texture support. Mipmap
   filtering support and demos for efficient blurring via gpu accelerated
   resolution pyramids. The new `BlurredMipmapDemo` employs/demonstrates OpenGL
   mip-map filtering to use image resolution pyramids for fast blurring of
   images, e.g., for certain types of gaze contingent displays.

*  MOGL OpenGL support updated to support most new OpenGL-2.1 extensions up
   to the ones added in August 2012.

*  Various other improvements, cleanups and bug fixes i can't remember.

[commit]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/commit/fde2c3f5e00dabd27fc83356659f8099c78c585f
