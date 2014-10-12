---
layout: page
title: Flavors and Versions
categories: getting-started
---

Historically, users could choose among two different branches of Psychtoolbox-3: `beta` and `stable`.

Since then the `stable` branch has fallen into disuse and has become
deprecated. Day-to-day development now occurs on GitHub, with the `beta` branch
in Subversion serving as the main distribution channel to our users.

| **`beta`**    | current, rolling releases of Psychtoolbox             |
| **`stable`**  | deprecated and unsupported branch, removed in 3.0.10  |

The **`beta`** branch provides the latest features, performance enhancements
and bug fixes. These features have been tested by the [developers][] on the
system configurations at their disposal and should be reasonably safe for real
world use.

However, there may be undiscovered bugs, and with the very limited resources
new stuff needs to see real world use to shake out remaining bugs. We rely on
*you* for the testing of new features and for feedback about problems or bugs.

Versioned Releases
------------------

The `beta` branch of PTB is normally updated for the purpose of introducing
bug fixes, new features or incremental improvements. Thus the `beta`
branch pushes out rolling releases, and the incremental updates are
reflected in their SVN revision number. 

Executing the command `PsychtoolboxVersion` should return the *version number,
flavor and revision number* of your current Psychtoolbox. The command also
prints a web URL, which points to the online change log where you can read in
detail what has changed between different revisions. You can use the info provided
by `PsychtoolboxVersion` to restore your installation to a given version, providing
the SVN revision number to our `DownloadPsychtoolbox` install script, useful for
documenting your research software and ensure reproducibility of the software environment.

Before any potentially disruptive changes are merged into the `beta` branch, we
tag and release a new version of Psychtoolbox following the versioning scheme
**`Psychtoolbox-3.x.y`**.  Examples of such disruptive changes would be the
discontinuation of support for an operating system, Matlab version, or a computer
hardware platform - anything that could introduce functional regressions into your
existing hardware and software environment. We recommend to stick with the `beta`
branch, unless you have good reason not to do so, as it is the only officially
tested and supported branch.

Previous Releases
-----------------

The following releases of old Psychtoolbox versions are available.

<small>There were some unfortunately numbered versions 1.0.x released earlier in the
development of PTB-3, but this numbering caused so much confusion with respect
to PTB Version 2 that we have now abandoned that system.</small>

`Psychtoolbox-3.0.11`
   : A snapshot of the code as of September 2014: This was the final 3.0.11 release
     before start of the 3.0.12 series. It was the last version that supported
     32-Bit Matlab on any operating system (specifically on Linux and Windows, as
     support for 32-Bit Matlab was cancelled already in 3.0.10). Going on, only
     64-Bit Octave and Matlab are supported on all operating systems, and only
     32-Bit Octave continues to be supported on Linux. This was also the last version
     to work on OSX versions older than 10.8 "Mountain Lion", and to be tested and
     supported on MS-Windows versions older than Windows-7. Going on, Windows XP
     and later still should work, but we won't test or optimize or provide any kind
     of support or bug fixes for anything older than Windows-7. Similarly we only
     provide official support for the very latest OSX version. Psychtoolbox-3.0.11
     is also the last release to use the GStreamer-0.10 legacy multi-media framework
     for movie playback, movie writing, video capture and video recording. Future
     releases use and require GStreamer-1.0 or later for multi-media functionality.

`Psychtoolbox-3.0.10`
   : A snapshot of the code as of July 2013: This was the final 3.0.10 release
     before start of the 3.0.11 series. It was the last version that supported
     32-Bit Matlab on OSX.

*To download and install the following legacy versions, use the
[`DownloadLegacyPsychtoolbox`][legacy-installer] function*

`Psychtoolbox-3.0.9`
   : A snapshot of the code as of May 2012: This was the final 3.0.9 release
     before start of the 3.0.10 series. It was the last version that supports
     Matlab versions older than V7.4 (a.k.a R2007a). It was also the last version
     to support Apple PowerPC hardware. Support for Apple’s Quicktime will be
     also phased out after this version, in favor of the much more modern, free
     and open-source cross-platform GStreamer multimedia framework, which will
     take over Quicktime’s duties. This was also the last version to support
     32-Bit GNU/Octave on MS-Windows and OSX.

`Psychtoolbox-3.0.8`
   : A snapshot of the code as of April 2011: This was the final 3.0.8 release
     before start of the 3.0.9 series with its new “mostly MIT” license model.

`Psychtoolbox-3.0.8-PreMatlab6.5`
   : A snapshot of the code as of late 2010: This was the last release that worked
     with Matlab versions before V6.5.

`Psychtoolbox-3.0.8-PreTiger`
   : A snapshot of the code as of February 2009: This was the last release
     that is (assumed, not tested!) to work properly in most parts on Mac OS X
     versions prior to 10.4 “Tiger”, i.e., 10.3 “Panther” and earlier. It was also
     the last release with support for GNU Octave versions prior to 3.2.0 on Mac
     OS and Linux.

`Psychtoolbox-3.0.7`
   : A snapshot of the code as of October 2006: Added basic and limited support
     for movie playback on OSX via Quicktime, some performance enhancements to the
     drawing functions and a few bug fixes. 

  [developers]: http://psychtoolbox.org/CurrentActiveDevelopers
  [legacy-installer]: https://raw.githubusercontent.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadLegacyPsychtoolbox.m
