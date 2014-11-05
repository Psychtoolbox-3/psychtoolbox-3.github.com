---
layout: post
title: Psychtoolbox 3.0.12 released
categories: news
author: kleinerm
---

The first BETA "Random acts of kindness" was relased at 5th October 2014
and started the new Psychtoolbox 3.0.12 series. Now, one month later,
after some stabilization and tweaking and some minor updates, and without
any user complaints so far, it is about time to announce it.

As usual, the complete develoment history can be found in our GitHub
repository. The release tag is "PTB_Beta-2014-11-06_V3.0.12", with the
full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2014-11-06_V3.0.12>

Changes with respect to version 3.0.11:

### System and software requirements

-   Only 64-Bit Windows-7 is officially supported. PTB only gets (infrequently
    and lightly) tested with Windows-7. It should also work with 64-Bit Windows-8
    and later and with 64-Bit Windows Vista and 64-Bit Windows-XP, but
    if you run into problems with those earlier or later systems you are
    on your own. Especially support for Windows-XP is expected to degrade
    due to lack of future testing and bug fixing. No care will be taken to
    prevent future development from breaking support for Windows XP or Vista.
    
    32-Bit versions of Windows will no longer work with Psychtoolbox 3.0.12.

-   64-Bit OSX version 10.8 "Mountain Lion" and later is needed for PTB to
    work at all, but only OSX 10.10 "Yosemite" is officially supported. No
    future testing, bug fixing or troubleshooting will be performed for any
    version but 10.10 "Yosemite".
    
-   All reasonably modern versions of 32-Bit and 64-Bit Linux should work.
    Primary development and testing is done on Ubuntu 14.04-LTS and 14.10,
    and compatible flavors, e.g, KUbuntu 14.04-LTS and KUbuntu 14.10. These
    are the officially supported Linux distributions. GNU/Debian version 7
    and upcoming version 8 are tested by the NeuroDebian team.
    
-   Matlab: 64-Bit Matlab on Linux, OSX and Windows. Current development and
    testing happens with R2012a but will probably be soon completely shifted
    to R2014b.
    
    32-Bit versions of Matlab are no longer working with Psychtoolbox 3.0.12.
    
-   GNU/Octave: On Linux, our "DownloadPsychtoolbox" installable version supports
    32-Bit and 64-Bit Octave version 3.8.x for Debian and Ubuntu. On OSX, our
    "DownloadPsychtoolbox" installable version supports Octave 3.8.0 - 3.8.2.
    
    If you get your Psychtoolbox for GNU/Debian or Ubuntu from NeuroDebian's
    repository then it will support whatever 32-Bit or 64-Bit version of Octave
    is officially shipping with your distribution - usually some Octave version
    between 3.4.0 and 3.8.x, depending on the age of your distribution.
    
    We do recommend upgrading your Linux distro to a release from the year 2014,
    as those will usually ship Octave 3.8 out of the box. Octve 3.8 features a
    Matlab like GUI for a higher level of convenience.
    
-   GStreamer: GStreamer-0.10.x is no longer supported. You must install GStreamer
    version 1.4.0 or later on Windows or OSX, GStreamer version 1.0.0 or later
    on Linux if you want to use any multi-media functionality like Video capture,
    Video recording, movie writing or movie playback.
    
-   PsychKinect support: Support for the Kinect now requires libfreenect version 0.5
    or later on Linux and OSX. Suitable versions of libfreenect will be automatically
    provided by NeuroDebian if you install Psychtoolbox for Linux from their repository.
    On OSX you can get a sufficiently recent version of libfreenect from HomeBrew.
    
### Major new features and improvements:

### All operating systems:

-   GStreamer 1.0 as new multi-media backend. Apart from fixing some bugs of
    GStreamer-0.10, this should make Psychtoolbox multi-media handling more
    future-proof, as GStreamer-1.x is in active development and supported, whereas
    GStreamer-0.10.x no longer receives and maintenance, support or bug fixes from
    its developers. GStreamer-1 supports more video codecs, support for deep color
    video formats and more efficient multi-threaded video decoding for popular
    formats like H264. The latter should provide performance gains on multi-core
    Mac OSX and Windows machines, so performance on those legacy operating systems
    should come a bit closer to what Linux users are enjoying since many years.
    
    Caveats: Video capture and recording is currently unsupported on MS-Windows
    due to missing video capture plugins in the current GStreamer-1.4 distribution
    for Windows. This will start working again when the GStreamer developers provide
    suitable plugins. Video capture on OSX is limited to what Apples AVFoundation and
    QuicktimeKit support. Specifically capture from DV camcorder cameras didn't work
    at all when testing under OSX 10.9. Audio-Video sync for video recording with
    USB webcams under OSX 10.9 wasn't great at all. The best video capture and recording
    experience is expected under Linux, just as in the past. Movie playback with some
    video codecs on Microsoft Windows with some Matlab versions can cause random
    crashes of Matlab. This has been infrequently observed during playback of H264 video,
    e.g., with Psychtoolbox `SimpleMovieDemo`. These don't happen always and are likely
    due to some incompatibility between some Matlab versions and GStreamer. There are
    no known problems wit any movie playback on OSX or Linux.
    
-   The `PsychKinect` driver now supports the XBOX Kinects and the original Kinect 1
    for Windows - on Linux and OSX. Kinect for Windows is not supported on MS-Windows.
    Kinect 2 is not supported at all at the moment. The driver can handle multiple
    simultaneous Kinects.

-   Stereo crosstalk reduction support, especially for frame sequential stereo modes by
    Diederick. Useful, e.g., to reduce crosstalk on NVidia's NVision shutter glasses. See
    help of `PsychImaging`.
    
-   Our MOGL OpenGL for Matlab and Octave low-level support now supports a large subset of
    OpenGL 4.5 functionality. Functionality of OpenGL versions more recent than version 2.1
    is supported via OpenGL extensions as in the past, but our support is now more complete
    wrt. the latest OpenGL 4.5 spec. E.g., Geometry Shaders do work now.
    
-   The Datapixx mex files for VPixx devices like Datapixx, Viewpixx and Propixx is now
    available with identical full feature set on all operating systems and supported Matlab
    and Octave versions. `PsychImaging` will now take care of especially large VBLANK intervals
    as used by those devices in frame sequential stereo modes.
    
-   Improvements and bug fixes to the `NetStation()` driver for EGI Netstation EEG systems.

-   Bug fixes and enhancements to `DrawFormattedText`.

-   The `RemapMouse` function can now also handle display rotation by Psychtoolbox panel fitter,
    ie., rotation generated by the `PsychImaging` functions `UseDisplayRotation` and `UsePanelFitter`
    can now be properly handled wrt. mouse input, as demonstrated in `PanelFitterDemo`.
    
-   Many bug fixes and improvements to demos, help texts or other documentation.

### GNU Linux

-   Support for Ubuntu 14.10 and compatible/derived flavors - tested with 64-Bit KUbuntu 14.10.
    `help SyncTrouble` points to a new set of example xorg.conf configuration files and
    explains how to install those in your system to optimize it for best visual stimulus
    onset timing and timestamping precision. This release has been tested on Ubuntu 14.04
    and KUbuntu 14.04 and KUbuntu 14.10 with X-Servers XOrg-1.15 and 1.16, Linux kernels
    3.13, 3.16 and later kernels on open-source radeon, nouveau and intel graphics drivers
    with multiple Radeon graphics cards, NVidia graphics cards and Intel graphics cards and
    shows excellent visual timing behaviour on all tested systems. Especially on Apple
    systems, the tested Linux distros outperformed OSX wrt. timing precision and reliability
    by large margins, sometimes up to 300x more precise.

-   Improved deep color 10 bpc framebuffer support on Linux. New 11 bpc and (up to) 16 bpc
    framebuffer support for AMD graphics cards when using the open-source graphics driver
    on a deep color capable HDMI or DisplayPort display device. Details of setup, limitations
    and capabilities for different systems are explained in the help text of `PsychImaging`.

### Apple OSX

-   Support for Mac OSX 10.10 "Yosemite". However, initial testing on two machines and
    user feedback suggests that 10.10 seems to be even more buggy and unsuitable for
    neuro-science applications than 10.9 and 10.8 were. None of the bugs present in OSX and
    known to me have been fixed by Apple, as far as initial testing goes. Visual timing
    and timestamping precision has degraded even further. Expect many new "Sync failures",
    as all attempts to workaround OSX flaws have failed. The `PsychtoolboxKernelDriver` is
    now even more important for precise visual timing, but no longer works by default on
    Intel GPUs. Forcing its use on Intel gpu's is possible but can cause serious system
    malfunctions on some Macintosh computers, with a small but non-zero probability of
    making your machine unbootable without the help of an Apple repair technician.
    In order to load the driver at all on OSX 10.10 for the supported NVidia and AMD gpus,
    you will need to disable kernel module verification in Apples OS. See "help PsychtoolboxKernelDriver" for instructions to do so at the downside of reducing system resilience against hackers
    and computer viruses.

-   Improved `PsychHID` for OSX: Now supports multiple parallel simultaneous keyboard queues,
    catching up a bit to the superior `PsychHID` for Linux. Now can cope with Apples broken
    HID keyboard handling on MacbookAir 2013 and later, making keyboard queues working again
    on the MacbookAir.
    
-   Support for Apple Retina displays. Visual stimulus onset timing and timestamping should
    work better now with such non-standard HiDPI display devices. Psychtoolbox will use its
    panel fitter by default to create backwards compatible behaviour to version 3.0.11, but
    with hopefully fixed visual onset timing, working around Apples Retina display hacks.
    A new `PsychImaging` task `UseRetinaResolution` allows to make use of the full resolution
    of Retina displays (typically twice the horizontal and vertical video resolution for 4
    times more pixels), at the performance impact caused by the much higher GPU rendering load.
    
-   Many new awful workarounds for broken Apple operating systems.
