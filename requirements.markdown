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

    GNU Linux is recommended. Also works on Apple Mac OS X (Intel) and Microsoft
    Windows (Intel).

-   *Runtime environment:*

    Matlab Version 7.4 R2007a or later, also GNU Octave version 3.2 or later on
    Linux and Octave version 3.6 on OS X.

    A cautious migration to 64-bit versions of Matlab and Octave is
    recommended, especially for users of OS X.

-   *Graphics card:*

    Recommended are any OpenGL 2.1 or better capable GPUs from AMD or NVidia.
    Modern Intel HD-Series graphics cards should work for moderately complex
    workloads. More recent OpenGL-3/4 GPUs may expose additional useful
    features. The absolute minimum requirement is OpenGL-1.2 support, but
    functionality will be limited with such old GPUs. 

    Do not buy PC laptops with hybrid-graphics, e.g., with NVidia Optimus
    technology! Their graphics timing behaviour will likely be wrong and there
    is no known way to fix this in software.

-   *Sound card:*

    On Linux and OS X, any card supported by the operating system should work
    well. On Windows, an ASIO capable audio card is absolutely required for
    research grade timing precision and low-latency.


Operating systems
-----------------

### Linux

GNU/Linux is fully supported on Intel compatible PCs and Apple Macintosh
computers under

-  Matlab 7.4 R2007a (32-bit and 64-bit), or later
-  GNU Octave 3.2 (32-bit and 64-bit), or later

Psychtoolbox should run well on any recent Linux distribution. Testing
and development however occurs mainly on the most recent Ubuntu Linux
releases.

It is recommended to keep up with the latest distribution releases or to stick
to the latest long-term support (LTS) Ubuntu release.

The [NeuroDebian project][neurodebian] is an effort to provide convenient
access to neuroscience-related software on the Debian and Ubuntu Linux
distributions. The NeuroDebian APT archives include a Psychtoolbox snapshot
release, which has been packaged to be ready-to-use with GNU Octave.

Recently NeuroDebian has begun to curate open-source packages [for Matlab as
well][neurodebian-matlab], and since provides two sets of packages, one for
Octave and one for Matlab.

As an older home-spun solution, the
[`DownloadAdditionsForNeuroDebian`][additions] script allows you to
automatically download our compiles for Matlab on top of the NeuroDebian Octave
package.

For details on these options, see the [Linux installation instructions][linux-install].

We generally recommend Linux as the operating system of choice for
demanding experimental setups, which require the highest timing
precision, precision for color or luminance displays, general
performance and flexibility.

### Apple Macintosh

Psychtoolbox is also being developed and tested under Apple Mac OS X.
Supported are

-   64-bit Matlab on OS X 10.6 "Snow Leopard" and later
-   64-bit Octave 3.6 and later on OS X 10.6 "Snow Leopard" and later

Compatibility tests have been run on OS X 10.6.8, and 10.7.4 with 64-bit
Matlab R2012a and on 10.7.4 with 64-Bit Octave 3.6.

Regular testing currently only happens on the latest version of 10.7
“Lion” with 64-Bit Octave 3.6, and with 64-bit Matlab R2012a, but more
recent OS X versions should work reasonably well for many tasks, according
to user reports.

The current toolbox version 3.0.11 releases are not supported under OS X 10.5
or earlier anymore. The last version that worked on OS X 10.4 and 10.5 and also
with 32-Bit versions of Matlab was v3.0.10. It can be downloaded by specifying
the special `flavor` parameter `Psychtoolbox-3.0.10` in our `DownloadPsychtoolbox`
downloader script.

The last version that worked on 10.3 can be downloaded by
specifying the special `flavor` parameter `Psychtoolbox-3.0.8-PreTiger`
in our `DownloadLegacyPsychtoolbox` legacy downloader script.

The PowerPC platform is no longer supported by the version 3.0.10
Psychtoolbox. If you need to use a PowerPC machine, stick to version
3.0.9.

In general, operating system versions 10.4 “Tiger” and 10.6 “Snow
Leopard” seem to be relatively unproblematic in use, i.e., most of the
many operating system bugs we found now have workarounds implemented in
Psychtoolbox. 10.5 “Leopard” was a rather buggy operating system,
especially for multi-display stimulus presentation and stereoscopic
stimulus presentation. 10.7 “Lion” and later mostly has restrictions in
the precision for visual stimulus timestamping due to various bugs in the
operating system. Please install the Psychtoolbox kernel driver to
resolve these issues (see [PsychtoolboxKernelDriver][docs-kerneldriver] or 
`>> help PsychtoolboxKernelDriver`).

### Windows

-   Matlab 32-bit or 64-bit, release 7.4 R2007a or later

    External requirements: Microsoft C runtime and GStreamer

If you choose to use Matlab, you may need to install Microsoft Visual C runtime
libraries to make it work, specifically `vcredist_x86.exe` or
`vcredist_x64.exe`. The installer should give you instructions on how to do
that if necessary.

Psychtoolbox-3 runs under Microsoft Windows XP, Windows Vista, Windows 7
and Windows 8.

We do aim to keep the toolbox working under these and future versions of
Windows, but full support for all features is a lower priority for us
than Linux or Mac OS X.

As of December 1, 2009, Windows Vista and Windows-7 have been tested for
basic compatibility with PTB-3. Precision of sound presentation hasn’t
been tested at all due to lack of suitable testing equipment. Test of
visual stimulus presentation on 3 test setups showed somewhat mixed
results, especially dual display presentation and presentation timing
were rather disappointing. We are aware that many people do run the
toolbox under Vista or Windows 7 and there were not many reports of
timing trouble so far.

We cannot however recommend Window 7 at all for dual-display stereo
stimulus presentation or for tasks with a need for high visual timing
precision. For some caveats with respect to Vista and later see [our FAQ
entry about Vista and Windows-7][faqvista]. These problems may be even worse
with Windows 8, although no systematic testing has been performed by us so far.

All in all you are worse off with Vista and later than with XP, so there is
no reason to switch to it. Those systems seem to provide less performance
than XP while at the same time posing higher hardware requirements.

Additional software
-------------------

#### Multimedia engine: GStreamer required

On **64-bit OS X**, installation of GStreamer is mandatory for movie playback,
movie recording, video capture and video recording. Quicktime is no longer
supported.

On **Linux** you also need GStreamer for these operations, but GStreamer is
a de-facto standard component that ships with all modern Linux distributions.

On **Windows** you must install [GStreamer][gstreamer]. The way we have to
link to the GStreamer libraries requires GStreamer to be installed even if
you don’t intend to use the multimedia features.

See [GStreamer][docs-gstreamer] (or `>> help GStreamer`) for installation
instructions for the different systems.

On **32-bit Mac OS X** legacy Psychtoolbox 3.0.10 used Apple Quicktime 7 for
movie playback, movie creation, video capture and recording. Quicktime is
installed on any OS X system by default. Psychtoolbox was able to also
optionally use GStreamer.

Basic hardware requirements
---------------------------

-   Intel PCs: Any Intel-compatible PC that is capable of running the
    32/64-bit versions of Microsoft Windows XP/Vista/Windows-7/Windows-8
    or 32/64 bit GNU/Linux.

-   Intel Macs: Any Intel-based Macintosh computer that is capable of
    running 64-Bit OS X 10.6 “Snow Leopard” or later, or 32/64 Bit GNU/Linux.

-   The Psychtoolbox distributed by the Debian project also supports
    other processor architectures, e.g., PowerPC, ARM, MIPS, Sun
    UltraSparc, IBM S/360 and some others.

Graphics hardware requirements
------------------------------

Basic Psychtoolbox functions should work on any OpenGL 1.2 capable
graphics card with at least 16 MB of video ram (VRAM). Fast stimulus
drawing and use of the more advanced features requires recent graphics
hardware. However, we do recommend at least OpenGL 2.1 capable graphics
hardware for full functionality and good performance.

In general, you should not try to skimp on the GPU, as performance of
your stimulus script and the types of visual stimuli you can create with
ease will depend much more on the horse power and features of your GPU
than on the performance of your CPU.

If you want to use all Psychtoolbox features at full performance and
precision, make sure to get a recent Direct3D 10 or 11 capable (a.k.a.
OpenGL 3 or 4 capable) graphics card from NVidia or AMD/ATI. Almost all
cards of the NVidia GeForce 8 series and later (e.g., 8600, 8800, 9600,
9800, GTX 280 etc.), as well as all cards of the AMD/ATI Radeon HD series
and later (HD 2400, 2600, 3000 series, 4000 series, etc.) and their corresponding
counterparts from the NVidia Quadro series and ATI FireGL / FirePro line
of cards are technically state-of-the-art and Psychtoolbox can take full
advantage of their features.

The latest generation of integrated Intel HD graphics cards, e.g., Intel HD
2000, HD 3000, as found in many modern “Intel Core” processors, provide decent
functionality, accuracy and performance for not too demanding tasks. They are
OpenGL-3 / Direct3D-10 compliant. Numeric precision is on par with recent
NVidia or AMD cards for most (but not all) accuracy tests that have been
executed on a Intel HD-3000 under OS X 10.7.4 Lion. Absolute graphics
performance is of course significantly lower than that of current discrete
NVidia or AMD cards. But for not too demanding visual stimulation paradigms,
these cards are now somewhat suitable.

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

[In depth: More detailed information and recommendations for graphics
hardware][gfxhw]

For dual-display work (e.g., binocular stereo stimulation), we strongly
recommend using dual-head or multi-head graphics adapters (i.e., *one*
card with two or more output connectors) instead of multiple separate
adapters. We expect dual/multi-head single-card performance to be higher
and the likelihood of graphics driver bugs to be lower. While separate
cards may work, we do not guarantee this and do not provide any support
for troubleshooting. Note that stereo work may benefit from the display
synchrony provided by some of the dual-head cards. Synchrony is usually
hard to achieve with separate cards. We also recommend to avoid Mac OS X
for dual display real-time stimulus presentation, as Apple seems to be
mostly incapable of and uninterested in implementing decent support for
high performance, tear-free dual display support. For static stimuli or
use as a control monitor, OS X may be good enough.

  [linux-install]: {{site.url}}/download#Linux
  [neurodebian]: http://neuro.debian.net
  [neurodebian-matlab]: http://neuro.debian.net/proj_matlab.html
  [additions]: http://docs.psychtoolbox.org/DownloadAdditionsForNeuroDebian
  [gstreamer]: http://gstreamer.freedesktop.org
  [docs-gstreamer]: http://docs.psychtoolbox.org/Gstreamer
  [docs-kerneldriver]: http://docs.psychtoolbox.org/PsychtoolboxKernelDriver
  [c++ runtime]: http://www.microsoft.com/downloads/details.aspx?familyid=766A6AF7-EC73-40FF-B072-9112BAB119C2&displaylang=en#filelist
  [faqvista]: http://psychtoolbox.org/FaqVista
  [gma950]: http://en.wikipedia.org/wiki/GMA_950
  [gfxhw]: {{site.url}}/graphics-requirements

