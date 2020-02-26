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
    under Windows are highly problematic! Use on Apple Mac OS X is still possible but _strongly discouraged_
    if you need any kind of reliable timing for visual stimulus presentation or precisely calibrated
    visual output, or use of special visual stimulators, e.g., from VPixx or CRS, or trustworthy
    visual stimulation at all, due to the large and growing number of bugs in the Apple operating system.

-   *Runtime environment:*

    64-Bit Matlab version R2019a or later (older versions may work), and GNU Octave version 3.8 or later version
    on Linux, and 64-Bit [Octave version 5.1.0 on OS X][Octave5OSX] [and on MS-Windows.][Octave5ForWindows]

-   *Graphics card:*

    Recommended are OpenGL 2.1 (or ideally better!) capable GPUs from AMD. Modern Intel graphics
    chips should also work well on Linux for more simple tasks with lower need for performance.

    **AMD GPUs are strongly recommended over NVidia GPUs on Linux and OSX**, as they
    allow use of high quality open-source graphics drivers on Linux, and of additional
    useful PTB features for vision science on Linux and also to some degree on OSX.
    The most well tested models are currently from the AMD "Polaris" gpu family, with
    the most exhaustive set of low-level features supported by Psychtoolbox on Linux.
    AMD "Vega" gpu family gpu's should provide the same quality and features, and have
    improved FreeSync support if you need it. They are expected to work well with
    Psychtoolbox, but not tested due to lack of hardware. The latest generation "Navi"
    gpu's may work, but are untested and lack support for special Psychtoolbox low-level
    features at the moment. So the sweet spot would be "Polaris", or "Vega" if you intend
    to use FreeSync for interesting visual stimulation paradigms that require Psychtoolbox
    VRR functionality.
    
    Only choose NVidia if you absolutely must for some very good reason, e.g., if you must
    use CUDA during visual stimulation. Note that we won't be able to help you much with
    problems caused by NVidia gpu's even on Linux, as we can't fix their proprietary
    graphics drivers!
    
    Modern Intel HD-Series graphics cards should work reliably for medium
    complexity workloads on Linux. Current OpenGL-3/4 GPUs may expose additional
    useful features. The absolute minimum requirement is OpenGL-1.2 support, but
    functionality and performance will be very limited with such old GPUs. 

    Try to avoid PC laptops with hybrid-graphics, e.g., with NVidia Optimus or
    AMD Enduro technology! Under MS-Windows the visual onset timing of the high
    performance gpu will very likely be wrong on most such laptops and there is no
    known way to fix this with software workarounds, so you might be restricted
    to the integrated low performance gpu. At least Intel integrated gpus are
    often _very buggy_ under MS-Windows, so you would be out of luck completely. The
    behavior on Linux is generally better: Many Laptops will work reliably with the high
    performance gpu and the open-source graphics drivers when combined with an
    Intel integrated gpu, e.g., models with older NVidia graphics cards and most AMD
    graphics cards. The most recent gpu models from NVidia are more difficult to set up
    and somewhat rather inflexible to use, due to limitations of their proprietary
    graphics drivers, restricting such Optimus setups to single-display visual stimulation
    only if the proprietary graphics drivers are in use. The
    combination of AMD integrated gpu + AMD discrete gpu currently doesn't work well
    at all. At least the lower performance integrated AMD graphics chips should work
    as a reliable fallback in such a scenario on Linux though. Read ["help HybridGraphics"][HybridGraphics],
    which provides up to date info.

-   *Sound card:*

    On Linux and OS X, any card supported by the operating system should work
    well, as well as built-in sound chips. On MS-Windows 7 to 10, sound cards should
    work reasonably well with Psychtoolbox 3.0.15 and later, but Windows 10 should
    provide enhanced precision and lower latency over Windows 7. On MS-Windows with
    Psychtoolbox version 3.0.14 and earlier, no precise or low latency sound output
    is possible anymore. [Click this link to find out why.][AudioHW]

Operating systems
-----------------

### Linux

GNU/Linux is fully supported on Intel compatible PCs and suitable Apple Macintosh
computers under

-  Matlab 64-bit, version R2019a and later versions. R2014b is also somewhat tested, older versions may work
-  GNU Octave 64-bit, versions 3.8, 4.0 and 4.2.
-  Additionally, Psychtoolbox from NeuroDebian supports 32-Bit and 64-Bit
   releases of whatever version of GNU Octave ships by default with your
   distribution, e.g., also Octave 3.6, 3.4 or 3.2 on older distributions,
   or Octave 4.4 and Octave 5.1 on recent distributions.

Psychtoolbox testing and development occurs mainly on the most recent Ubuntu
Linux LTS releases or flavors of them like e.g., KUbuntu, XUbuntu, LUbuntu ...

NeuroDebian tests and supports PTB also on Debian GNU/Linux. According to
user reports, Psychtoolbox seems to work reasonably well on Linux Mint, Arch
Linux, Gentoo, and Fedora 24/25. We can't provide much support on other distros
than Ubuntu LTS flavors due to lack of time and resources.

It is recommended to stick to the latest long-term support (LTS) Ubuntu release,
currently 18.04.3-LTS, if you want the most well tested setup.

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
We strongly discourage use of Apple macOS for anything but entertainment
and education purposes.

### Apple macOS - Not recommended!

Psychtoolbox is also being developed and tested under Apple Mac OS X.
Psychtoolbox should "work" in principle on

-  64-bit Matlab R2014b on OS X 10.11 "El Capitan" and later. Tested with R2019a on macOS 10.13 "High Sierra".
-  64-bit Octave v5.1.0 on OS X 10.11 "El Capitan" and later. As of 2019,
   [you will need to get Octave 5.1.0 from a package manager like HomeBrew][Octave5OSX]
   or MacPorts, as standalone binary installers are not available yet.

Limited testing currently only happens on the latest version of OS X 10.13.6
“macOS High Sierra” with 64-Bit Octave 5.1.0, and with 64-bit Matlab R2019a. This
is the only somewhat supported version of OS X at this point in time. _macOS is
the most buggy and hazardous operating system you could use for visual stimulation,
or DAQ digital/analog i/o, so running real data collection using macOS will likely
bring you a world of pain (and possibly irreproducible research)_.

Toolbox version 3.0.14 and later releases do not work under OS X 10.10
or earlier anymore. The last working version on OS X 10.10 was v3.0.13.
The last version that worked on OS X 10.9 and 10.8 was v3.0.12. The last
version that worked on OS X 10.7 and 10.6 was v3.0.11. The last version
that worked on OS X 10.5 and 10.4 and also with 32-Bit versions of Matlab
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

-   Matlab 64-bit. Currently tested with release R2019a.
    External mandatory requirements: Microsoft C MSVC 2015-2019 runtime and GStreamer 1.16 MSVC or later.

-   [GNU Octave 5.1.0, 64-Bit. Installation of GStreamer _before_ installation
    of Psychtoolbox is mandatory on GNU Octave or the mex files will not work.
    The current download location for official Octave-5.1.0 64-Bit is reached by
    clicking this link.][Octave5ForWindows]

If you choose to use Matlab, you may need to install Microsoft Visual C runtime
libraries to make it work, specifically `vcredist_x64_2015-2019.exe`. The installer should
give you instructions on how to do that if necessary.

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

We do aim to keep the toolbox working under these and future versions of
Windows, but full support for all features is a lower priority for us
than Linux.

As of October 1, 2016, Windows-7 and Windows-10 have been tested for
basic compatibility with PTB-3. Test of
visual stimulus presentation on 3 test setups showed somewhat mixed
results, especially dual display presentation and presentation timing
were rather disappointing. In general Windows 7 seems to be workable for
pure single display setups, fragile on any multi-display setup. Windows 10
seems to be also workable for single display stimulation on a dual display setup,
ie. one display for the operator and its GUI, one display for visual stimulation,
provided it is properly configured, e.g., the visual stimulus monitor selected as
"main monitor" or "primary display", and either no HiDPI displays or careful
configuration of such a setup with HiDPI displays.

We cannot however recommend Window at all for dual-display stereo
stimulus presentation or for tasks with a need for high visual timing
precision. For some caveats with respect to Vista and later see [our FAQ
entry about Vista and Windows-7][faqvista].

Generally we recommend switching to a modern version of Linux, e.g., a flavor of
Ubuntu 18.04-LTS.

Additional software
-------------------

#### Multimedia engine: GStreamer 1.16 or later required on Windows and macOS

Installation of GStreamer version 1.16 or later is mandatory for movie playback,
movie recording, video capture and video recording. Multimedia functions won't
work on **OSX** without GStreamer being installed. If you want
to use Psychtoolbox for visual stimulation on **Windows** you will _have_ to install
GStreamer first, even if you do not need any multimedia functions, or Psychtoolbox
won't work. GStreamer 1.16.0 MSVC variant or later is needed, earlier versions or
MinGW variants will not work.

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

-   Intel Macs: _Not recommended!_
    Any Intel-based Macintosh computer that is capable of
    running 64-Bit OS X 10.11 “El Capitan” or later, or 32/64 Bit GNU/Linux.
    However: At this point in time, most NVidia graphics cards have broken
    visual stimulation timing under macOS. Most AMD graphics cards under
    OS X 10.12 and later have broken visual stimulation timing under macOS,
    and Intel graphics chips also seem to have trouble under at least macOS
    10.13 "High Sierra". If you install Psychtoolbox 3.0.16, these timing
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

-   [RaspberryPi models 2B and 3 under the most recent Raspbian operating system.][Raspbian]
    The RaspberryPi 2B is actively tested for compatibility and works well
    for not too demanding visual and auditory stimulation tasks, USB i/o
    and digitial i/o via the programmable GPIO pins. The Pi model 3 is not
    tested yet, but expected to work just as well as the model 2B.

Graphics hardware requirements
------------------------------

Basic Psychtoolbox functions should work on any OpenGL 1.2 capable
graphics card with at least 16 MB of video ram (VRAM), with the mentioned
operating system specific restrictions in mind, ie., somewhat broken on
Windows multi-display and almost completely broken on macOS. Fast stimulus
drawing and use of the more advanced features requires recent graphics
hardware. However, we do _strongly recommend_ at least OpenGL 2.1 capable
graphics hardware for full functionality and good performance. For optimal
performance and functionality on Linux we recommend AMD or Intel graphics
over NVidia graphics, due to the high quality open-source drivers for AMD
and Intel graphics.

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
  [c++ runtime]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/raw/master/Psychtoolbox/PsychContributed/vcredist_x64_2015-2019.exe
  [faqvista]: http://psychtoolbox.org/FaqVista
  [gma950]: http://en.wikipedia.org/wiki/GMA_950
  [gfxhw]: /graphics-requirements
  [Octave5ForWindows]: https://ftpmirror.gnu.org/octave/windows/octave-5.1.0-w64-installer.exe
  [Octave5OSX]: https://formulae.brew.sh/formula/octave
  [Raspbian]: https://www.raspberrypi.org/
  [HybridGraphics]: https://raw.githubusercontent.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/PsychDocumentation/HybridGraphics.m
  [AudioHW]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/wiki/Hardware:-Audio-Devices
