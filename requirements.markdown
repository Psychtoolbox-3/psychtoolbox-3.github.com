---
layout: page
title: System Requirements
categories: getting-started
---

#### Contents

-  TOC be here
{:toc #toc}
{::options auto_ids="true" toc_levels="2..3"/}


Short version
-------------

-   *Operating system:*

    GNU Linux is _strongly_ recommended. Also works on Apple Mac OS X (Intel) and Microsoft
    Windows (Intel), but will be much less well supported by the developers and may have
    restrictions in functionality, reliability, performance and precision for some features,
    compared to Psychtoolbox running on a modern Linux distribution.

-   *Runtime environment:*

    64-Bit Matlab version 7.14 (R2012a) or later, and GNU Octave version 3.8 or later on
    Linux, and 64-Bit Octave version 4.0.x on OS X and MS-Windows.

-   *Graphics card:*

    Recommended are OpenGL 2.1 (or better) capable GPUs from AMD or NVidia.
    Modern Intel HD-Series graphics cards should work reliably for medium
    complex workloads on Linux. More recent OpenGL-3/4 GPUs may expose additional
    useful features. The absolute minimum requirement is OpenGL-1.2 support, but
    functionality and performance will be limited with such old GPUs. 

    Try to avoid PC laptops with hybrid-graphics, e.g., with NVidia Optimus or
    AMD Enduro technology! Under MS-Windows the visual onset timing of the high
    performance gpu will likely be wrong on most such laptops and there is no
    known way to fix this with software workarounds, so you might be restricted
    to the integrated low performance gpu. At least Intel integrated gpus are
    often _very buggy_ under MS-Windows, so you would be out of luck. The
    behavior on Linux is a bit better: Some Laptops will work reliably with the high
    performance gpu and the open-source graphics drivers when combined with an
    Intel integrated gpu, e.g., models with older NVidia and AMD graphics cards. The
    most recent gpu models from NVidia and AMD are still problematic., or difficult
    to set up, or unworkable. The combination of AMD integrated gpu + AMD discrete gpu
    currently doesn't work well at all. At least the lower performance integrated Intel
    and AMD graphics chips should work as a reliable fallback on Linux though. Read
    ["help HybridGraphics"][HybridGraphics], which provides up to date info.

-   *Sound card:*

    On Linux and OS X, any card supported by the operating system should work
    well. On Windows, an ASIO capable audio card is absolutely required for
    research grade timing precision and low-latency.


Operating systems
-----------------

### Linux

GNU/Linux is fully supported on Intel compatible PCs and Apple Macintosh
computers under

-  Matlab 64-bit, release v7.14 - R2012a and later versions.
-  GNU Octave 64-bit, versions 3.8 and 4.0.
-  Additionally, Psychtoolbox from NeuroDebian supports 32-Bit and 64-Bit
   releases of whatever version of GNU Octave ships by default with your
   distribution, e.g., also Octave 3.6, 3.4 or 3.2 on older distributions.

Psychtoolbox should run well on any recent Linux distribution. Testing
and development however occurs mainly on the most recent Ubuntu Linux LTS
releases or flavors of them like e.g., KUbuntu, XUbuntu, LUbuntu ...

It is recommended to keep up with the latest distribution release or to stick
to the latest long-term support (LTS) Ubuntu release, currently 16.04-LTS.

[Psychtoolbox also works with GNU Octave on the RaspberryPi 2B and later at
least with the Debian flavor Raspbian.][Raspbian]

The [NeuroDebian project][neurodebian] is an effort to provide convenient
access to neuroscience-related software on the Debian and Ubuntu Linux
distributions. The NeuroDebian APT archives include a Psychtoolbox snapshot
release, which has been packaged to be ready-to-use with GNU Octave.

Recently NeuroDebian has begun to curate open-source packages [for Matlab as
well][neurodebian-matlab], and since provides two sets of packages, one for
Octave ("octave-psychtoolbox-3") and one for Matlab ("matlab-psychtoolbox-3").

For details on these options, see the [Linux installation instructions][linux-install].

We generally recommend Linux as the operating system of choice for
demanding experimental setups, which require the highest timing
precision, precision for color or luminance displays, general
performance and flexibility. Our support for fixing bugs and other
issues on other operating systems than Linux will be very limited.

### Apple Macintosh

Psychtoolbox is also being developed and tested under Apple Mac OS X.
Psychtoolbox should work on

-   64-bit Matlab on OS X 10.10 "Yosemite" and later. Tested with R2012a.
-   64-bit Octave v4.0 on OS X 10.10 "Yosemite" and later.

Regular testing currently only happens on the latest version of OS X 10.11
“El Capitan” with 64-Bit Octave 4.0, and with 64-bit Matlab R2012a. This is
the only somewhat supported version of OS X at this point in time.

The current toolbox version 3.0.13 releases do not work under OS X 10.9
or earlier anymore. The last version that worked on OS X 10.8 and 10.9
was v3.0.12. The last version that worked on OS X 10.6 and 10.7 was
v3.0.11. The last version that worked on OS X 10.4 and 10.5 and also
with 32-Bit versions of Matlab was v3.0.10. Those old and unsupported
versions of Psychtoolbox can be downloaded by specifying the special `flavor`
parameter `Psychtoolbox-3.0.12` or `Psychtoolbox-3.0.11` or
`Psychtoolbox-3.0.10` in our [`DownloadPsychtoolbox`][current-installer]
downloader script.

The PowerPC platform is no longer supported by the version 3.0.10
Psychtoolbox. If you need to use a PowerPC machine, stick to version
3.0.9.

In general, operating system versions 10.4 “Tiger” and 10.6 “Snow
Leopard” seemed to be relatively unproblematic in use, i.e., most of the
many operating system bugs we found now have workarounds implemented in
Psychtoolbox. 10.5 “Leopard” was a rather buggy operating system,
especially for multi-display stimulus presentation and stereoscopic
stimulus presentation. 10.7 “Lion” and later mostly has restrictions in
the precision for visual stimulus timestamping due to various bugs in the
operating system. Please install the Psychtoolbox kernel driver to
resolve some of these issues (see [PsychtoolboxKernelDriver][docs-kerneldriver] or 
`>> help PsychtoolboxKernelDriver`).

### Windows

Psychtoolbox should work on

-   Matlab 64-bit. Currently tested with release 7.14 R2012a.
    External requirements: Microsoft C runtime and GStreamer.

    Various Matlab versions show instable behavior with GStreamer unless
    they are used without the Graphical user interface and Java, ie. in
    matlab.exe -nojvm mode. Matlab can also cause problems on HiDPI "Retina"
    style displays.

-   [GNU Octave 4.0, 64-Bit. Installation of GStreamer _before_ installation
    of Psychtoolbox is mandatory on GNU Octave or the mex files will not work.
    The current download location for inofficial Octave-4 64-Bit builds is
    reached by clicking this link.][Octave4ForWindows]

If you choose to use Matlab, you may need to install Microsoft Visual C runtime
libraries to make it work, specifically `vcredist_x64.exe`. The installer should
give you instructions on how to do that if necessary.

Psychtoolbox-3 still runs under Microsoft Windows XP, Windows Vista, Windows 7
and Windows 8/8.1, but we don't actively test for compatibility with any system
but Windows 10 and won't provide any bug fixes or troubleshooting help for any
issues that can't be shown to be also present on Windows 10. Specifically, moving
away from Windows XP, Vista and Windows 8/8.1 is strongly recommended. Windows 7
should continue to work without major problems at this point in time, but we don't
frequently test for this.

We do aim to keep the toolbox working under these and future versions of
Windows, but full support for all features is a lower priority for us
than Linux.

As of October 1, 2016, Windows-7 and Windows-10 have been tested for
basic compatibility with PTB-3. Precise sound presentation requires a
native ASIO sound card and card specific careful configuration. Test of
visual stimulus presentation on 3 test setups showed somewhat mixed
results, especially dual display presentation and presentation timing
were rather disappointing. In general Windows 7 seems to be workable for
pure single display setups, fragile on any multi-display setup. Windows 10
seems to be workable for single display stimulation on a dual display setup,
ie. one display for the operator and its GUI, one display for visual stimulation,
provided it is properly configured, e.g., the visual stimulus monitor
selected as "main monitor" or "primary display", no HiDPI displays or careful
configuration of such a setup.

We cannot however recommend Window 7 at all for dual-display stereo
stimulus presentation or for tasks with a need for high visual timing
precision. For some caveats with respect to Vista and later see [our FAQ
entry about Vista and Windows-7][faqvista]. These problems are even worse
with Windows 8, although no systematic testing has been performed by us so far.

Generally we recommend switching to a modern version of Linux, e.g., a flavor of
Ubuntu 16.04-LTS.

Additional software
-------------------

#### Multimedia engine: GStreamer 1.x required

Installation of GStreamer version 1.0 or later is mandatory for movie playback,
movie recording, video capture and video recording. Multimedia functions won't
work on **Windows** or **OSX** without GStreamer being installed. If you want
to use Psychtoolbox with GNU Octave on **Windows** you will _have_ to install
GStreamer even if you do not need any multimedia functions, or Psychtoolbox
won't work.

On **Linux** you also need GStreamer, but GStreamer is a de-facto standard
component that ships with all modern Linux distributions.

See [GStreamer][docs-gstreamer] (or `>> help GStreamer`) for installation
instructions for the different systems.

#### Microsoft Kinect support on Linux and OSX: libfreenect-0.5 required

For use of your PsychKinect / PsychKinectCore driver on Linux or OSX,
at least version 0.5 of libfreenect is needed. See `>> help InstallKinect`
for instructions.

Basic hardware requirements
---------------------------

-   Intel PCs: Any Intel-compatible PC that is capable of running the
    64-bit versions of Microsoft Windows Windows-7/Windows-10, or the
    32-bit or 64-bit versions of GNU/Linux.

-   Intel Macs: Any Intel-based Macintosh computer that is capable of
    running 64-Bit OS X 10.10 “Yosemite” or later, or 32/64 Bit GNU/Linux.

-   [RaspberryPi models 2B and 3 under the most recent Raspbian operating system.][Raspbian]
    The RaspberryPi 2B is actively tested for compatibility and works well
    for not too demanding visual and auditory stimulation tasks, USB i/o
    and digitial i/o via the programmable GPIO pins. The Pi model 3 is not
    tested yet, but expected to work.

-   The Psychtoolbox distributed by the Debian project also supports
    other processor architectures, e.g., PowerPC, ARM, MIPS, Sun
    UltraSparc, IBM S/360 and some others. However, only the Intel and
    RaspberryPi builds receive testing and support from us at this time.

Graphics hardware requirements
------------------------------

Basic Psychtoolbox functions should work on any OpenGL 1.2 capable
graphics card with at least 16 MB of video ram (VRAM). Fast stimulus
drawing and use of the more advanced features requires recent graphics
hardware. However, we do _strongly recommend_ at least OpenGL 2.1 capable
graphics hardware for full functionality and good performance.

In general, you should not try to skimp on the GPU, as performance of
your stimulus script and the types of visual stimuli you can create with
ease will depend much more on the horse power and features of your GPU
than on the performance of your CPU.

If you want to use all Psychtoolbox features at full performance and
precision, make sure to get a recent Direct3D 10 or 11 capable (a.k.a.
OpenGL 3 or 4 capable) graphics card from AMD or NVidia. Almost all
cards of the NVidia GeForce 8 series and later (e.g., 8600, 8800, 9600,
9800, GTX 280 etc.), as well as all cards of the AMD/ATI Radeon HD series
and later (HD 2400, 2600, 3000 series, 4000 series, etc.) and their corresponding
counterparts from the NVidia Quadro series and ATI FireGL / FirePro line
of cards are technically state-of-the-art and Psychtoolbox can take full
advantage of their features.

The latest generation of integrated Intel HD graphics cards, e.g., Intel HD
2000, HD 3000, as found in many modern “Intel Core” processors, provide decent
functionality, accuracy and performance for not too demanding tasks *on Linux*.
*Use on other operating systems than Linux will usually go much less well*. These cards
are OpenGL-3 / Direct3D-10 compliant. Numeric precision is on par with recent
NVidia or AMD cards for most (but not all) accuracy tests that have been
executed on a Intel HD card under Linux. Absolute graphics performance is of
course significantly lower than that of current discrete NVidia or AMD cards.
But for not too demanding visual stimulation paradigms, these cards are now
somewhat suitable.

Older Intel graphics cards are problematic for all but the most trivial visual
stimulation tasks: While the Intel GMA X3100 series cards and similar are also
Direct3D 10 compliant in theory, in practice they suffer from limitations.
Users of Intel-based Macs should be aware that some Macs (e.g., old Intel
Mac Book) use a *built-in Intel GMA* graphics adaptor. The GPUs of the GMA-950
series are known to have *very low graphics performance* and a *very restricted
feature set*. They are cheap and sub-standard by any definition. See [this
Wikipedia article][gma950] for further information.

Products from Matrox, Via and S3 or from other niche vendors are not
recommended. As Matrox and S3 seem to have mostly retreated from the 3D
graphics market, most of their products are not a good choice for OpenGL
based applications like Psychtoolbox. Even the products that nominally
claim to support hardware accelerated OpenGL, have a pretty limited
feature set and performance.

For dual-display work (e.g., binocular stereo stimulation), we strongly
recommend using dual-head or multi-head graphics adapters (i.e., *one*
card with two or more output connectors) instead of multiple separate
adapters. We expect dual/multi-head single-card performance to be higher
and the likelihood of graphics driver bugs to be lower. While separate
cards may work, we do not guarantee this and do not provide any support
for troubleshooting. Note that stereo work may benefit from the display
synchrony provided by some of the dual-head cards. Synchrony is usually
hard to achieve with separate cards. We also recommend to avoid Mac OS X
and MS-Windows for dual display real-time stimulus presentation. Apple
seems to be mostly incapable of or uninterested in implementing decent
support for high performance, tear-free dual display support. For static
stimuli or use as a control monitor, OS X may be good enough. MS-Windows
has equally severe trouble with multi-display visual stimulation, and
often even for single-display stimulation on a multi-display setup.

  [linux-install]: /download#Linux
  [legacy-installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadLegacyPsychtoolbox.m
  [current-installer]: https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadPsychtoolbox.m
  [neurodebian]: http://neuro.debian.net
  [neurodebian-matlab]: http://neuro.debian.net/proj_matlab.html
  [gstreamer]: http://gstreamer.freedesktop.org
  [docs-gstreamer]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/GStreamer.m
  [docs-kerneldriver]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychDocumentation/PsychtoolboxKernelDriver.m
  [c++ runtime]: http://www.microsoft.com/downloads/details.aspx?familyid=766A6AF7-EC73-40FF-B072-9112BAB119C2&displaylang=en#filelist
  [faqvista]: http://psychtoolbox.org/FaqVista
  [gma950]: http://en.wikipedia.org/wiki/GMA_950
  [gfxhw]: /graphics-requirements
  [Octave4ForWindows]: http://www.tatsuromatsuoka.com/octave/Eng/Win/
  [Raspbian]: https://www.raspberrypi.org/
  [HybridGraphics]: https://raw.githubusercontent.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/PsychDocumentation/HybridGraphics.m
