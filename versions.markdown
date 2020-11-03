---
layout: page
title: Flavors and Versions
categories: getting-started
---

By default, Psychtoolbox provides the so called **`beta`** branch or flavor.
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

*To download and install the following versions, use the
[`DownloadPsychtoolbox`][standard-installer] function*

`Psychtoolbox-3.0.16`
   : A snapshot of the code as of beginning of November 2020: This was the final 3.0.16 release
     before start of the 3.0.17 series. 3.0.16 was the last version to support:


      * 64-Bit Octave-5 for MS-Windows and Apple macOS.


      * On Windows: GStreamer versions older than 1.18.0 MSVC, or any GStreamer MinGW builds. Now only GStreamer 1.18 MSVC builds are supported.


      * Official Linux Ubuntu 16.04 LTS support. However, Linux Ubuntu 16.04 LTS or other distributions with at least GStreamer 1.8 should continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible.


      * Official macOS older than 10.15.7 support. However, older versions should continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible.


      * Official Windows-7, Windows-8 and Windows-8.1 support. However, older versions than Windows-10 should currently continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible.

`Psychtoolbox-3.0.15`
   : A snapshot of the code as of beginning of August 2019: This was the final 3.0.15 release
     before start of the 3.0.16 series. 3.0.15 was the last version to support:
     
     
      * 64-Bit Octave-4.4.1 for MS-Windows.

      
      * On Windows: GStreamer versions older than 1.16.0, or any GStreamer MinGW builds. Now only MSVC builds are supported. This was the last version that allowed to avoid installing GStreamer on Windows if one does not need multi-media functionality.
     
     
      * 64-Bit Octave-4.4.1 for OSX.
      
      
      * Linux Ubuntu 14.04 LTS or other distributions with GStreamer versions older than 1.4.0.


`Psychtoolbox-3.0.14`
   : A snapshot of the code as of beginning of September 2018: This was the final 3.0.14 release
     before start of the 3.0.15 series. 3.0.14 was the last version to support:
     
     
      * 64-Bit Octave-4.2 for MS-Windows.
     
     
      * 64-Bit Octave-4.2 for OSX.
      
      
      * ASIO ® pro-audio support for MS-Windows. <small>ASIO is a trademark and software of Steinberg Media Technologies GmbH.</small>
      [Update: All versions of Psychtoolbox lost all ASIO ® support in December 2018, so you will
      need to use Psychtoolbox 3.0.15 or later if you want a WASAPI based replacement for reasonably
      good sound support on Windows.][AudioHW]


`Psychtoolbox-3.0.13`
   : A snapshot of the code as of end of December 2016: This was the final 3.0.13 release
     before start of the 3.0.14 series. 3.0.13 was the last version to support:
     
     
      * 64-Bit Octave-4.0 for MS-Windows.
     
     
      * 64-Bit Octave-4.0 for OSX.
     
      
      * Mac OSX 10.10 "Yosemite".
   
   
      Future beta releases will only support/work on:
   
   
      * 64-Bit Octave-4.2 for Windows and OSX. Octave 3.8 and later on Linux.
      
      
      * 64-Bit Matlab on all operating systems, R2012a or later is recommended, earlier versions may or may not continue to work, but are no longer tested or supported in case of trouble.
      
      
      * OSX 10.11 El Capitan and OSX 10.12 Sierra. Only macOS Sierra is tested and somewhat supported in case of trouble.

`Psychtoolbox-3.0.12`
   : A snapshot of the code as of June 2016: This was the final 3.0.12 release
     before start of the 3.0.13 series. 3.0.12 was the last version to support:
     
     
      * 32-Bit Octave-4 for MS-Windows.
     
     
      * 64-Bit Octave-3.8 for OSX.
     
      
      * Mac OSX 10.8 "Mountain Lion" and OSX 10.9 "Mavericks".
   
   
      Future beta releases will only support/work on:
   
   
      * 64-Bit Octave-4 for Windows and OSX.
      
      
      * 64-Bit Matlab on all operating systems, R2012a or later is recommended, earlier versions may or may not continue to work, but are no longer tested or supported in case of trouble.
      
      
      * OSX 10.10 Yosemite and 10.11 El Crapitan. Only El Crapitan is tested and somewhat supported in case of trouble.
      
      
      * On Linux i will no longer provide mex files for 32-Bit Octave for Intel machines for direct download from us. However, NeuroDebian / Debian upstream / Ubuntu upstream will continue to provide these mex files in a convenient fashion in their "app-stores", so this is not really a drawback, just something to be aware of.

`Psychtoolbox-3.0.11`
   : A snapshot of the code as of September 2014: This was the final 3.0.11 release
     before start of the 3.0.12 series. It was the last version that supported
     32-Bit Matlab on any operating system (specifically on Linux and Windows, as
     support for 32-Bit Matlab for OSX was cancelled already in 3.0.10). Going on, only
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

*Automated download and installation of the following legacy versions is no longer
possible!* Click on the download link for a version, if such a link is provided,
to download a zip file which approximately contains the code corresponding to that
version. Unzip the file, then cd() into the Psychtoolbox subfolder of the extracted
Psychtoolbox-3 folder. Then run the SetupPsychtoolbox function to set that old copy
up for use. You will need a compatible Matlab/Octave version and operating system
version for this to work. If you can't find a download link, ask on the Psychtoolbox
user forum for help.

`Psychtoolbox-3.0.9`
   : A snapshot of the code as of May 2012: This was the final 3.0.9 release
     before start of the 3.0.10 series. It was the last version that supports
     Matlab versions older than V7.4 (a.k.a R2007a). It was also the last version
     to support Apple PowerPC hardware. Support for Apple’s Quicktime will be
     also phased out after this version, in favor of the much more modern, free
     and open-source cross-platform GStreamer multimedia framework, which will
     take over Quicktime’s duties. This was also the last version to support
     32-Bit GNU/Octave on MS-Windows and OSX.
     [`Download link for 3.0.9 zip file`][ptb-3.0.9]

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
  [standard-installer]: https://raw.githubusercontent.com/Psychtoolbox-3/Psychtoolbox-3/master/Psychtoolbox/DownloadPsychtoolbox.m
  [ptb-3.0.9]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/Psychtoolbox-3.0.9.zip
  [AudioHW]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/wiki/Hardware:-Audio-Devices 
