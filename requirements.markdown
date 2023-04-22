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

    GNU Linux is _strongly_ recommended. Also works on Microsoft Windows 10 (Intel), but will
    be much less well supported by the developers and may have restrictions in functionality,
    reliability, performance and precision for some features, compared to Psychtoolbox running
    on a modern Linux distribution. Especially multi-display setups and HiDPI Retina displays
    under Windows are highly problematic! Use on Apple macOS is possible but _strongly discouraged_
    if you need any kind of reliable timing for visual stimulus presentation or precisely calibrated
    visual output, or use of special visual stimulators, e.g., from VPixx or CRS, or trustworthy
    visual stimulation at all, due to the large and growing number of bugs in the Apple operating system.
    macOS 11 is completely untested and not officially supported yet.

-   *Runtime environment:*

    64-Bit Matlab version R2022b or later (older versions will likely work, but are no longer tested
    for compatibility or supported by us in case of trouble), and GNU Octave version 5.2 or later versions
    on Linux, and 64-Bit [Octave version 8.2.0 on macOS][OctavemacOS] [and Octave 7.3.0 on MS-Windows.][OctaveForWindows]

-   *Graphics card:*

    Recommended are OpenGL 2.1 (or ideally better!) capable GPUs from AMD. Modern Intel graphics
    chips will also work well **on Linux, not on Windows** for more simple tasks with lower need
    for performance.

    **AMD GPUs are strongly recommended over NVidia GPUs on Linux and macOS**, as they
    allow use of high quality open-source graphics drivers on Linux, and of additional
    useful PTB features for vision science on Linux (and also to some degree on macOS, for
    old AMD GPUs older than AMD Vega).
    **On Linux, please do not install the AMD proprietary amdgpu-pro driver**, but simply
    stick to the high qualiy amdgpu driver which is already installed on any new Linux
    installation (batteries included!), iow. if you don't do anything, you'll do the right
    thing.
    
    The most well tested AMD models are currently from the AMD "Polaris" gpu family, with
    the most exhaustive set of low-level features supported by Psychtoolbox on Linux.
    AMD "Vega" family gpu's should provide the same quality and features, and additionally
    have improved FreeSync support, if you need it. They are expected to work well with
    Psychtoolbox on Linux, according to testing by one lab so far. The latest generation "Navi"
    gpu's seem to also work well, according to some user reports, but are not yet tested
    by the developers due to lack of hardware, and they do lack support for some special,
    but rarely needed, Psychtoolbox low-level debug
    features at the moment. So the sweet spot would be "Polaris", or "Vega" if you intend
    to use FreeSync for interesting visual stimulation paradigms that require Psychtoolbox
    VRR functionality. AMD "Raven Ridge" gpu's, integrated into AMD Ryzen processors, are
    also well tested and known to work under Linux and Windows-10. As "Raven Ridge" uses a
    "Vega" graphics core at its heart, this is another indicator that "Vega" should work fine.

    Only choose NVidia if you absolutely must for some very good reason, e.g., if you must
    use CUDA during visual stimulation. Note that we won't be able to help you much with
    problems caused by NVidia gpu's **even on Linux**, as we can't debug or fix their
    proprietary graphics drivers in any meaningful way!

    Modern Intel HD-Series graphics cards should work reliably for medium
    complexity workloads on Linux. Current OpenGL-3/4 GPUs may expose additional
    useful features. The absolute minimum requirement is OpenGL-1.2 support, but
    functionality and performance will be very limited with such old GPUs, and using
    graphics cards with only functionality older than OpenGL-2.1 has not been tested
    by the developers in years.

    **Try to avoid PC laptops with hybrid-graphics, e.g., with NVidia Optimus or
    AMD Enduro technology!** Under MS-Windows the visual onset timing of the high
    performance gpu will very likely be wrong on most such laptops, and there is no
    known way to fix this with software workarounds, so you might be restricted
    to the integrated low performance gpu. At least Intel integrated gpus are
    often _very buggy_ under MS-Windows, so you would be out of luck completely! The
    behavior on Linux is generally much better, often with precise timing and good
    performance, but it depends on the gpu combination. In any case, even on Linux,
    more manual setup is needed to make things work, and some combinations will still
    only work with very reduced performance, e.g., AMD iGPU's with non-AMD dGPU's, or
    older AMD iGPU's. The only plug & play solution even under Linux is a single-gpu
    machine.: Read ["help HybridGraphics"][HybridGraphics], which provides up to date
    info about capabilities, limitations and setup for different gpu combinations.

-   *Sound card:*

    On Linux and macOS, any card supported by the operating system should work
    well, as well as built-in sound chips. On MS-Windows 7 to 10, sound cards should
    work reasonably well with Psychtoolbox 3.0.15 and later, but Windows 10 should
    provide enhanced precision and lower latency over Windows 7. On MS-Windows with
    Psychtoolbox version 3.0.14 and earlier, no precise or low latency sound output
    is possible anymore. [Click this link to find out why.][AudioHW]

Operating systems
-----------------

### Linux

GNU/Linux is fully supported on Intel compatible PCs and suitable (== older) Apple
Macintosh computers under

-  Matlab 64-bit, version R2022b. Older versions likely work, but are no longer
   tested or testable by us due to lack of access.
-  GNU Octave 64-bit, versions 5.2, 6.1 - 7.3.
-  Additionally, Psychtoolbox from NeuroDebian supports 32-Bit and 64-Bit
   releases of whatever version of GNU Octave ships by default with your
   distribution, e.g., also Octave 3.2 to 4.4 on older distributions, or
   Octave 5.x, 6.x and 7.x on recent distributions.

Psychtoolbox testing and development occurs mainly on the most recent Ubuntu
Linux LTS releases or flavors of them, currently Ubuntu 20.04.6-LTS. Distributions
older than Ubuntu 20.04-LTS are no longer supported since Psychtoolbox 3.0.18. We
recommend Ubuntu 22.04.2-LTS at this time.

NeuroDebian tests and supports PTB also on Debian GNU/Linux. According to
user reports, Psychtoolbox seems to work reasonably well on Linux Mint, Arch
Linux, Gentoo, and Fedora. We can't provide much support on other distros than
Ubuntu LTS flavors due to lack of time and resources.

It is recommended to stick to the latest long-term support (LTS) Ubuntu release,
currently 22.04 -LTS, if you want the most well tested and well supported setup.

[Psychtoolbox also works with GNU Octave on the RaspberryPi 2B, 3, 4, 400 at least
with the Debian flavor Raspbian (also known as RaspberryPi OS).][Raspbian].

The [NeuroDebian project][neurodebian] is an effort to provide convenient
access to neuroscience-related software on the Debian and Ubuntu Linux
distributions. The NeuroDebian APT archives include a Psychtoolbox snapshot
release, which has been packaged to be ready-to-use with GNU Octave.

NeuroDebian curates some open-source neuroscience packages [for Matlab as
well][neurodebian-matlab], and provides two sets of packages, one for
Octave ("octave-psychtoolbox-3") and one for Matlab ("matlab-psychtoolbox-3").

For details on these options, see the [Linux installation instructions][linux-install].

**We generally strongly recommend Linux** as the operating system of choice for
demanding experimental setups, which require the highest timing
precision, precision for color or luminance displays, general
performance and flexibility. Our support for fixing bugs and other
issues on other operating systems than Linux will be very limited.
We strongly discourage use of Apple macOS for anything but entertainment
and education purposes.

### Apple macOS - Not recommended!

Psychtoolbox is also being developed and tested under Apple macOS 12.
Psychtoolbox should "work" in principle on

-  64-bit macOS 12.6 "Monterey", maybe macOS 10.14 - macOS 11 (no longer tested), maybe partially
   macOS 10.11-10.13 (no longer tested).
-  64-bit Matlab R2022b, likely older recent versions upwards of R2014b, but those are untested.
-  64-bit Octave v8.2 and v8.1, probably also v6.4-v7.3 (expected to work, but untested).
-  As of 2023, [you will need to get Octave 8.2 from a package manager like HomeBrew][OctavemacOS]
   as standalone binary installers are not available yet.

Limited testing currently only happens on a version of macOS 12.6
“macOS Monterey” with 64-Bit Octave 8.2 from HomeBrew, and with 64-bit Matlab R2022b.

Monterey is the only somewhat supported version of macOS at this point in time.
Psychtoolbox is compatible with Monterey in principle, and Monterey is the only
currently tested system, but Monterey has fantastic new bugs and flaws. Also note
that Apple stated that the only version of macOS that receives all their security
updates is the very latest version of macOS, which would be macOS 13 Ventura. We
do not officially test or support macOS 13 yet due to lack of recources caused by
lack of funding.

Catalina introduced many new flaws inherited by macOS 11 and macOS 12, e.g., a
slow-down of keyboard input by a factor of 5x, and various trouble wrt. keyboard
input, sound input, and video capture, thanks to Catalina's awful new security design
-- Prepare for lots of hassle if you choose Catalina, you have been warned!
_macOS is the most buggy and hazardous operating system you could use for visual
stimulation, or DAQ digital/analog i/o, so running real data collection using macOS
will likely bring you a world of pain (and possibly irreproducible research)_.

macOS Mojave was possibly a better working choice, although it is no longer tested by us
and unknown if it is still fully compatible with Psychtoolbox 3.0.19. The fact that it is no
longer developed or supported by Apple means that Apple will no longer break it with
respect to our needs, but it is now an attractive target for viruses and hackers,
a security hazard! Choose your poison...

**macOS 13 Ventura is not officially supported or tested at all at the moment!**
**macOS 11/12/13 on machines with Apple's new ARM based SoC's, e.g., the Apple M1 SoC,
are not working with Psychtoolbox natively at all in any suitable way for data collection.
There is no timeline for fixing this anytime soon. It is unclear if this is fixable at all,
given the challenging and disruptive changes Apple made on Apple Silicon, especially switching
from industry standard AMD, Intel and NVidia graphics to Apples own proprietary graphics chip.
But also due to the disappointing lack of financial support from most of our users, we con't
have the funds to investigate this any further at the moment.
It is possible to run Ubuntu Linux for ARM in a Virtual machine on Apple M1 for training
and education purpose, according to a user report, ie. not for data collection, only for
learning on Linux. It is also possible to somewhat run Psychtoolbox on macOS 11/12/13, but
with completely broken visual stimulation timing. May be good enough for basic training
purposes though.**
[See this link for reference about the current state.][AppleM1]

Toolbox version 3.0.14 and later releases do not work under macOS 10.10
or earlier anymore. The last working version on macOS 10.10 was v3.0.13.
The last version that worked on macOS 10.9 and 10.8 was v3.0.12. The last
version that worked on macOS 10.7 and 10.6 was v3.0.11. The last version
that worked on macOS 10.5 and 10.4 and also with 32-Bit versions of Matlab
was v3.0.10. Those old and unsupported versions of Psychtoolbox can be
downloaded by specifying the special `flavor` parameter `Psychtoolbox-3.0.13`
or `Psychtoolbox-3.0.12` or `Psychtoolbox-3.0.11` or `Psychtoolbox-3.0.10` in
our [`DownloadPsychtoolbox`][current-installer] downloader script.

The PowerPC platform is no longer supported by the version 3.0.10
Psychtoolbox. If you need to use a PowerPC machine, stick to version
3.0.9.

In general, only operating system versions 10.4 “Tiger” and 10.6 “Snow
Leopard” seemed to be relatively unproblematic in use, i.e., most of the
many operating system bugs we found now have workarounds implemented in
Psychtoolbox. 10.5 “Leopard” was a rather buggy operating system,
especially for multi-display stimulus presentation and stereoscopic
stimulus presentation. 10.7 “Lion” and later mostly has restrictions in
the precision for visual stimulus timestamping due to various bugs in the
operating system. Please install the Psychtoolbox kernel driver to help
resolve at least some of these issues on AMD and NVidia graphics cards
(see [PsychtoolboxKernelDriver][docs-kerneldriver] or 
`>> help PsychtoolboxKernelDriver`).

### Windows

Psychtoolbox should work on

-   Matlab 64-bit. Currently tested and supported with release R2022b.
    External mandatory requirements: Microsoft C MSVC 2015-2019 runtime and
    GStreamer 1.20.5 MSVC or later. Installation of GStreamer _before_ installation
    of Psychtoolbox is mandatory on Matlab or the Screen mex file will not work.

-   [GNU Octave 7.3.0, 64-Bit. Installation of GStreamer _before_ installation
    of Psychtoolbox is mandatory on GNU Octave or the Screen mex file will not work.
    The current download location for official Octave-7.3.0 64-Bit is reached by
    clicking this link.][OctaveForWindows]

If you choose to use Matlab, you may need to install Microsoft Visual C runtime
libraries to make it work, specifically `vcredist_x64_2015-2019.exe`. The installer should
give you instructions on how to do that if necessary, ie. on install failure. The
Psychtoolbox/PsychContributed/ subfolder contains the neccessary `vcredist_x64_2015-2019.exe`
executable for your convenience in such a case.

Psychtoolbox-3.0.19 is expected to fail to work soon on Windows-7 / 8 / 8.1. Only tested
on Windows 10 22H2 at the moment.

Psychtoolbox-3.0.17 - 3.0.18 is no longer officially supported for Windows-7 / 8 / 8.1. The
current expectation is that it still mostly works on these systems, but just as with
v3.0.16, only Windows-10 releases from 2021 (21H2 edition specifically) are tested and
supported in case of trouble, and some functionality like sound output should be better
on Windows-10, other functions like HDR High Dynamic Range display support will only work
on recent Windows-10.

Psychtoolbox-3.0.16 no longer works on Microsoft Windows XP, should continue to work
on Windows Vista and later, but just as with v3.0.15, only Windows-10 is tested and
supported in case of trouble.

Psychtoolbox-3.0.15 still worked under Microsoft Windows XP, Windows Vista, Windows 7
and Windows 8/8.1, but we don't actively test for compatibility with any system
but Windows 10 and won't provide any bug fixes or troubleshooting help for any
issues that can't be shown to be also present on Windows 10. Specifically, moving
away from Windows XP, Vista and Windows 8/8.1 is strongly recommended. Windows 7
should continue to work without major problems at this point in time, but we don't
test for this anymore. For best audio support, Windows 10 is strongly recommended.

We do aim to keep the toolbox working under these and future versions of Windows, but
full support for all features is a lower priority for us than Linux. Without the kind
of access to the source code and use of an open-source development process like on
Linux, it is also simply not possible to make improvements to the operating system
itself if needed, or to fix various bugs or even diagnose bugs for development of
workarounds. It is hit and miss...

We cannot recommend Window at for dual-display stereo stimulus presentation, HiDPI
setups, or for tasks with a need for high visual timing precision.

Generally we recommend switching to a modern version of Linux, e.g., a flavor of
Ubuntu 22.04-LTS.

Additional software
-------------------

#### Multimedia engine: At least GStreamer 1.20.5 required on Windows and macOS

Installation of at least GStreamer version 1.20.5 is mandatory for movie playback,
movie recording, video capture and video recording. Multimedia functions won't
work on **macOS** without GStreamer 1.18.5 or later being installed. Neither will high
quality text rendering work, unless you use Octave instead of Matlab. If you want to use
Psychtoolbox for visual stimulation on **Windows** you will _have_ to install
GStreamer first, even if you do not need any multimedia functions, or Psychtoolbox
won't work. GStreamer 1.20.5 MSVC variant or later is needed, earlier versions or
MinGW variants will not work on Windows.

On **Linux** you also need GStreamer, but GStreamer is a de-facto standard
component that ships with all modern Linux distributions. GStreamer 1.8 should work,
GStreamer 1.16 will work better, and GStreamer 1.18 is required for full convenient
support for HDR movie playback, whereas GStreamer 1.16 will need some "hand-holding"
by user scripts for more limited HDR playback support.

See [GStreamer][docs-gstreamer] (or `>> help GStreamer`) for installation
instructions for the different systems.

#### Microsoft Kinect support on Linux and macOS: libfreenect-0.5 required

For use of your PsychKinect / PsychKinectCore driver on Linux or macOS,
at least version 0.5 of libfreenect is needed. See `>> help InstallKinect`
for instructions. Kinect support on macOS is expected to still work, but deprecated.

Basic hardware requirements
---------------------------

-   Intel PCs: Any Intel-compatible PC that is capable of running the
    64-bit versions of Microsoft Windows-10, or the 64-bit versions of
    GNU/Linux Ubuntu 20.04 LTS or later. Ubuntu 22.04 LTS is recommended,
    as Ubuntu 20.04 LTS support will be phased out in the near future due
    to lack of resources.

-   Intel Macs: _Not recommended!_
    Any Intel-based Macintosh computer that is capable of running 64-Bit macOS
    12.6 “Monterey”, or a 64 Bit GNU/Linux distribution.
    However: At this point in time, most NVidia graphics cards have broken
    visual stimulation timing under macOS. Most AMD graphics cards under
    macOS 10.12 and later have broken visual stimulation timing under macOS,
    and Intel graphics chips also seem to have trouble under at least macOS
    10.13 "High Sierra". If you install Psychtoolbox 3.0.16 or later, these timing
    problems will be worked around at least for standard precision 8 bit per
    color framebuffers on many gpu + display combinations. Higher precision
    framebuffers are still unfixably broken, and some machines may still have
    problems, e.g., the new MacBookPro 2019 16 inch. So for visual stimulation
    there essentially doesn't exist any supported Apple hardware that would work
    acceptably under macOS in all configurations.

    Old hardware may perform fine under Linux. Apple MacBook's or MacBookPro's
    from the year 2016 or later are known to be mostly unusable with Linux for
    practical purposes, as basic things like wifi, suspend/resume or audio won't
    work. Any current Apple hardware with Apple's T2 security processor will
    not even allow accessing the internal disc drive - and thereby won't allow
    installation of Linux on the internal drive.
    _For these reasons we don't recommend use of any modern Apple hardware._

-   Apple ARM Macs, e.g., Apple M1: _Broken! Do not use!_

-   [RaspberryPi models 2B, 3, 4, 400 under the most recent Raspbian operating system.][Raspbian]
    The RaspberryPi 2B and 400 are actively tested for compatibility and works well
    for not too demanding visual and auditory stimulation tasks, USB i/o
    and digitial i/o via the programmable GPIO pins. The Pi model 3 is not
    tested, but expected to work just as well as the model 2B. Pi models 4 and 400
    are substantial improvements over the older models in hardware capabilities.

Graphics hardware requirements
------------------------------

Basic Psychtoolbox functions should work in theory on any OpenGL 1.2 capable
graphics card with at least 16 MB of video ram (VRAM), with the mentioned
operating system specific restrictions in mind, ie., somewhat broken on
Windows multi-display and broken on macOS for non-trivial use cases. Fast stimulus
drawing and use of the more advanced features requires recent graphics
hardware. However, we do _strongly recommend_ at least OpenGL 2.1 capable
graphics hardware for full functionality and good performance. Older graphics
cards are no longer tested.

For optimal performance and functionality on Linux we recommend AMD or Intel graphics
over NVidia graphics, due to the high quality open-source drivers for AMD
and Intel graphics. For advanced functionality like fine-grained timing via
FreeSync or Displayport adaptive sync, choose AMD. Ditto for HDR display
support.

In general, you should not try to skimp on the GPU, as performance of
your stimulus script and the types of visual stimuli you can create with
ease will depend much more on the horse power and features of your GPU
than on the performance of your CPU.

The recent generation of integrated Intel HD graphics cards, e.g., Intel HD
2000, HD 3000 etc., as found in many modern “Intel Core” processors, provide decent
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
hard to achieve with separate cards. We also recommend to avoid Mac macOS
and MS-Windows for dual display real-time stimulus presentation. Apple
seems to be mostly incapable of or uninterested in implementing decent
support for high performance, tear-free dual display support. For static
stimuli or use as a control monitor, macOS may be good enough. MS-Windows
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
  [c++ runtime]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychContributed/vcredist_x64_2015-2019.exe
  [gma950]: http://en.wikipedia.org/wiki/GMA_950
  [gfxhw]: /graphics-requirements
  [OctaveForWindows]: https://ftpmirror.gnu.org/octave/windows/octave-7.3.0-w64-installer.exe
  [OctavemacOS]: https://formulae.brew.sh/formula/octave
  [Raspbian]: https://www.raspberrypi.org/
  [HybridGraphics]: https://raw.githubusercontent.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/PsychDocumentation/HybridGraphics.m
  [AudioHW]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/wiki/Hardware:-Audio-Devices
  [AppleM1]: https://psychtoolbox.discourse.group/t/using-toolbox-with-big-sur-and-m1-macbook/3599/17
