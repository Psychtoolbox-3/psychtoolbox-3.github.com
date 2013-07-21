---
layout: post
title: PTB beta “Rotten Apples” release 2012-06-01 (Start of Psychtoolbox 3.0.10)
categories: news
author: kleinerm
---

[Psychtoolbox-3/Psychtoolbox-3@92809a33][commit] at [GitHub](https://github.com/Psychtoolbox-3/Psychtoolbox-3)

“Rotten Apples” starts the new Psychtoolbox Version 3.0.10 series.

The almost only new feature in this release is support for 64-Bit Matlab
under Apple MacOSX.

### Minimum system requirements for OSX/Apple:

-   An Intel based Apple Macintosh computer.
-   For 32-Bit OSX PTB: OSX 10.4.11 “Tiger” and later are still
    supported.
-   For 64-Bit OSX PTB: Absolute minimum is OSX 10.5.8 “Leopard”, with
    functionality and performance restrictions.
-   For 64-Bit OSX PTB: OSX 10.6 “Snow Leopard” and later should support
    all functionality without restrictions.

Basic 64 Bit compatibility testing happened on 10.5.8 with Matlab
R2010b-SP1, 10.6.8 with R2012a and 10.7.4 with R2012a. Future testing
will happen on 10.7.x Lion with R2012a, with very infrequent basic
testing on 10.5.8 Leopard with R2010b.

Support for using PTB on OSX on Apple PowerPC computers has been
removed. If you want to keep your old PowerPC useable with PTB you’ll
need to stick to the deprecated and unsupported V 3.0.9 PTB.

On Microsoft Windows, support for Matlab versions older than V7.4 -
R2007a has been completely removed. Windows-2000 and earlier is no
longer tested for compatibility with PTB.

On other systems, support for Matlab older than 7.4 - R2007a is no
longer guaranteed. The mex files would still work, but we will no longer
keep M-Files compatible with older Matlab versions.

If you want to use old Matlab versions, stick to the old V3.0.9 PTB, but
realize that this version is no longer supported by us in any way.

You won’t be able to upgrade to 3.0.10 via UpdatePsychtoolbox. Instead
you will need to download a complete fresh copy of PTB via
DownloadPsychtoolbox. The updater will provide you with further
instructions after a call to UpdatePsychtoolbox. Alternatively you can
download a fresh DownloadPsychtoolbox script from our Wiki. A new
installer script DownloadLegacyPsychtoolbox allows to downgrade to - or
stick with - older PTB’s of Version 3.0.9 or earlier if you want to run
on ancient hardware or Matlab versions.

PTB revision numbers, as reported by the PsychtoolboxVersion() command
for an old PTB installation have no meaning once you’ve upgraded to V
3.0.10, ie., the mapping of numbers to actual code has changed. This
means that the SVN revision number no longer uniquely defines the
software you have installed. Instead the combination of version number,
e.g., 3.0.10 and revision number does. The reason for this is that we
moved our code hosting for the new 3.0.10 series from GoogleCode to
GitHub, and our underlying version control system from Subversion to
Git.

Psychtoolbox on 64-Bit OSX now requires the free and open-source
GStreamer framework for movie playback, movie writing, video capture and
video recording - “help GStreamer” for installation instructions. The
32-Bit PTB on OSX will continue to use Apple Quicktime as a default for
a limited amount of time - until we have GStreamer support for it as
well, after which Quicktime will become optional, with GStreamer as
default. I consider Quicktime in maintenance mode from now on. Only
critical bugs regarding it will be fixed, but no future enhancements or
new features for it are planned

Psychtoolbox on Windows will switch to GStreamer as default with one of
the next beta releases, Quicktime will be made optional or possibly
completely removed on Windows if maintaining it turns out to be too much
work.

### Other changes in this beta release:

-   Some improvements to color and gamma calibration code by David
    Brainard.

-   The 64-Bit Psychtoolbox on OSX now also enables floating point
    textures and frame buffers for high color precision stimulus display
    and GPU computing on the latest generations of Intel graphics
    hardware, ie., the Intel HD 3000 integrated GPU’s found in recent
    MacBooks, MacBookPro and MacBook Air. Hardware functionality of
    these GPUs seems to have improved enough in the latest hardware
    generations to make them viable for more demanding tasks. Some of
    our software tests show good precision, comparable to discrete state
    of the art AMD or NVidia GPU’s, whereas some other tests still show
    some deficits, and no hardware testing with photometers etc. has
    been performed to see how well these gpu’s work for high precision
    stimuli beyond the frame buffer - ie. if the new goodness actually
    reaches the display correctly.

Intel HD graphics series support will be added for other operating
systems and 32-Bit configurations in a future ptb release.

### Much deserved credits for the OSX 64-Bit port go to:

Thanks to Prof. Heinrich Buelthoff at the Max Planck Institute for
Biological Cybernetics in Tuebingen, Germany, for supporting the work on
the 64-Bit port - and most other significant improvements to PTB
throughout the last six years, by letting me spend some of my work time
on this time intense “hobby”.

Thanks to Prof. Keith Schneider at the University of York, Canada, for
donating an almost new Apple MacBookPro, thereby allowing to work on a
64-Bit OSX port in a much more pain free manner.

Thanks to Ian Andolina from UCL London for help in initial testing of
the 64-Bit port.

Thanks to Linus Torvalds for inventing the wonderful Git version control
system and to GitHub for our free Git hosting. Git is a wonderful tool
for preventing nervous breakdowns and reducing crying fits and rage
against the machine during software development.

Absolutely no thanks to various unknown people working at Apple and
Mathworks for reasons too many and too horrifying to mention.

[commit]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/commit/92809a33
