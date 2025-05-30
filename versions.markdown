---
layout: page
title: Flavors and Versions
categories: getting-started
---

Versioned Releases
------------------

Psychtoolbox is normally updated for the purpose of introducing bug fixes, new
features or incremental improvements. New releases usually habe a bump in the
4th version number, the `z` in `3.x.y.z`.

Executing the command `PsychtoolboxVersion` should return the *version number,
flavor and revision number* of your current Psychtoolbox. The command also
prints a web URL, which points to the online change log where you can read in
detail what has changed between different revisions. *Since 8th January 2024,
this may no longer be the case for new Psychtoolbox downloads and updates.*

Before any potentially disruptive changes are released, we tag and release a new
version of Psychtoolbox with the `y` bumped following the versioning scheme
**`Psychtoolbox-3.x.y`**. Examples of such disruptive changes would be the
discontinuation of support for an operating system, Matlab version, or a computer
hardware platform - anything that could introduce functional regressions into your
existing hardware and software environment. We recommend to keep up with the latest
release, unless you have good reason not to do so, as it is the only officially
tested and supported branch.

Previous Releases
-----------------

The following releases of old Psychtoolbox 3.x.y versions are available.

*To download and install the following versions, go to our GitHub repository
and checkout or download the correspondlingly named Git branch. Or simply download
the linked zip file with the latest release of a given 3.x.y branch, if any is linked,
or click on the link to the release page for that version and navigate from there.*

`Psychtoolbox-3.0.21`
   : [A snapshot of the code as of 28th May 2025: This was the final 3.0.21 release
     before start of the 3.0.22 series. 3.0.21 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.21.0)

      * Ubuntu 20.04 LTS and Debian GNU/Linux 11. It still works in the 3.0.21.0 release, but is unsupported in case of trouble.
      Note that Ubuntu 20.04-LTS has reached end-of-life at the end of May 2025. Future Psychtoolbox-3.0.22 requires Debian 12 or
      Ubuntu 22.04.5 LTS or one of its siblings and derivates, or later versions of these distributions.

     Required 64-Bit GStreamer 1.22.5 MSVC on Microsoft Windows for both Matlab and Octave. GStreamer 1.18.6 or later recommended on macOS.

     [Download link for zip file for 3.0.21.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/download/3.0.21.0/3.0.21.0.zip)

`Psychtoolbox-3.0.20`
   : [A snapshot of the code as of 30th March 2025: This was the final 3.0.20 release
     before start of the 3.0.21 series. 3.0.20 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.20.4)

      * Going forward, Ubuntu 20.04 LTS still works in the 3.0.21.0 release, but is unsupported in case of trouble, and may stop working
        with any future release without warning. Note that Ubuntu 20.04-LTS will reach end-of-life by the end of April 2025.

     Required 64-Bit GStreamer 1.22.5 MSVC on Microsoft Windows for both Matlab and Octave. GStreamer 1.18.6 or later recommended on macOS.

     This was the first version that was not free of cost to use on Apple macOS and Microsoft Windows.
     It required a paid license key for macOS and Windows.

     *We do not recommend use of Psychtoolbox 3.0.20, but instead recommend use of at least Psychtoolbox 3.0.21.0 if
     you are on macOS or Windows. The license management has substantial improvements in 3.0.21.0, which is otherwise
     identical to the final 3.0.20.4 release in every aspect.*

     [Download link for zip file for 3.0.20.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/download/3.0.20.4/3.0.20.4.zip)

`Psychtoolbox-3.0.19`
   : [A snapshot of the code as of 14th December 2024: This was the final 3.0.19 release
     before start of the 3.0.20 series. 3.0.19 was the last version to support](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.19.16):

      * Last version tested on macOS 12. Future versions may or may not work on the macOS 10.13-10.15 and macOS 11.x/12.x operating systems.

      * Going forward, Ubuntu 20.04 LTS still works for a little while, but testing happens mostly only on Ubuntu 22.04-LTS and 24.04-LTS.

     Required 64-Bit GStreamer 1.22.5 MSVC on Microsoft Windows for both Matlab and Octave. GStreamer 1.18.6 or later recommended on macOS.

     This was the last version that was free of cost to use on Apple macOS and Microsoft Windows.
     Future versions will require a paid license key for macOS and Windows, whereas the Linux versions
     remain free to use until future notice.

     [Download link for zip file for 3.0.19.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/download/3.0.19.16/3.0.19.16.zip)

`Psychtoolbox-3.0.18`
   : [A snapshot of the code as of 17th February 2023: This was the final 3.0.18 release
     before start of the 3.0.19 series. 3.0.18 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.18.13)

      * 64-Bit Octave-6.3 and 6.4 for MS-Windows and Apple macOS.

      * Minimal support for Microsoft Windows 7 and 8. Future versions will fail to work correctly on anything but Windows-10 or later.

      * Last version tested on macOS 10.15. Future versions may or may not work on the macOS 10.x and macOS 11 operating systems.

      * RaspberryPi OS 10. Going forward, only OS 11 is supported on 32-Bit ARM.

      * Ubuntu Linux 20.04 LTS tested. Going forward, Ubuntu 20.04 LTS still works, but testing happens mostly only on Ubuntu 22.04-LTS.

     Requires 64-Bit GStreamer 1.18.5 MSVC on Microsoft Windows for both Matlab and Octave. GStreamer 1.18 recommended on macOS.

     [Download link for zip file for 3.0.18.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.18.zip)

`Psychtoolbox-3.0.17`
   : [A snapshot of the code as of beginning of October 2021: This was the final 3.0.17 release
     before start of the 3.0.18 series. 3.0.17 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.17.12)


      * 64-Bit Octave-6.1 and 6.2 for MS-Windows and Apple macOS.


      * 64-Bit Octave-3.x and 4.x for GNU/Linux.


      * Ubuntu Linux 18.04 LTS support. Going forward, only Ubuntu 20.04 LTS and later are supported.


      * Due to a bug, this version only runs on macOS 10.14 Mojave and later, instead of 10.11 El Capitan and later.

     Requires 64-Bit GStreamer 1.18 MSVC on Microsoft Windows for both Matlab and Octave. GStreamer 1.18 recommended on macOS.

     [Download link for zip file for 3.0.17](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.17.zip)

`Psychtoolbox-3.0.16`
   : [A snapshot of the code as of beginning of November 2020: This was the final 3.0.16 release
     before start of the 3.0.17 series. 3.0.16 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/3.0.16.8)


      * 64-Bit Octave-5 for MS-Windows and Apple macOS.


      * On Windows and macOS: GStreamer versions older than 1.18.0 MSVC, or any GStreamer MinGW builds. Now only GStreamer 1.18 MSVC builds are supported.


      * Official Linux Ubuntu 16.04 LTS support. However, Linux Ubuntu 16.04 LTS or other distributions with at least GStreamer 1.8 should continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible.


      * Official macOS older than 10.15.7 support. Older macOS versions may continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible. Hope is that macOS 10.11 El Capitan and later should probably still work at least in parts.


      * Official Windows-7, Windows-8 and Windows-8.1 support. However, older versions than Windows-10 should currently continue to work with v3.0.17, but are no longer tested or guaranteed to stay compatible.

     [Download link for zip file for 3.0.16.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.16.zip)

`Psychtoolbox-3.0.15`
   : [A snapshot of the code as of beginning of August 2019: This was the final 3.0.15 release
     before start of the 3.0.16 series. 3.0.15 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/PTB_Beta-2019-07-25_V3.0.15)
     
     
      * 64-Bit Octave-4.4.1 for MS-Windows.

      
      * On Windows: GStreamer versions older than 1.16.0, or any GStreamer MinGW builds. Now only MSVC builds are supported. This was the last version that allowed to avoid installing GStreamer on Windows if one does not need multi-media functionality.
     
     
      * 64-Bit Octave-4.4.1 for OSX.
      
      
      * Linux Ubuntu 14.04 LTS or other distributions with GStreamer versions older than 1.4.0.

     [Download link for zip file for 3.0.15.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.15.zip)

`Psychtoolbox-3.0.14`
   : [A snapshot of the code as of beginning of September 2018: This was the final 3.0.14 release
     before start of the 3.0.15 series. 3.0.14 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/PTB_Beta-2018-05-26_V3.0.14)
     
     
      * 64-Bit Octave-4.2 for MS-Windows.
     
     
      * 64-Bit Octave-4.2 for OSX.
      
      
      * ASIO ® pro-audio support for MS-Windows. <small>ASIO is a trademark and software of Steinberg Media Technologies GmbH.</small>
      [Update: All versions of Psychtoolbox lost all ASIO ® support in December 2018, so you will
      need to use Psychtoolbox 3.0.15 or later if you want a WASAPI based replacement for reasonably
      good sound support on Windows.][AudioHW]

     [Download link for zip file for 3.0.14.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.14.zip)

`Psychtoolbox-3.0.13`
   : [A snapshot of the code as of end of December 2016: This was the final 3.0.13 release
     before start of the 3.0.14 series. 3.0.13 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/PTB_Beta-2016-12-06_V3.0.13)
     
     
      * 64-Bit Octave-4.0 for MS-Windows.
     
     
      * 64-Bit Octave-4.0 for OSX.
     
      
      * Mac OSX 10.10 "Yosemite".
   
   
      Future beta releases will only support/work on:
   
   
      * 64-Bit Octave-4.2 for Windows and OSX. Octave 3.8 and later on Linux.
      
      
      * 64-Bit Matlab on all operating systems, R2012a or later is recommended, earlier versions may or may not continue to work, but are no longer tested or supported in case of trouble.
      
      
      * OSX 10.11 El Capitan and OSX 10.12 Sierra. Only macOS Sierra is tested and somewhat supported in case of trouble.

     [Download link for zip file for 3.0.13.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.13.zip)

`Psychtoolbox-3.0.12`
   : [A snapshot of the code as of June 2016: This was the final 3.0.12 release
     before start of the 3.0.13 series. 3.0.12 was the last version to support:](https://github.com/Psychtoolbox-3/Psychtoolbox-3/releases/tag/PTB_Beta-2016-05-14_V3.0.12)
     
     
      * 32-Bit Octave-4 for MS-Windows.
     
     
      * 64-Bit Octave-3.8 for OSX.
     
      
      * Mac OSX 10.8 "Mountain Lion" and OSX 10.9 "Mavericks".
   
   
      Future beta releases will only support/work on:
   
   
      * 64-Bit Octave-4 for Windows and OSX.
      
      
      * 64-Bit Matlab on all operating systems, R2012a or later is recommended, earlier versions may or may not continue to work, but are no longer tested or supported in case of trouble.
      
      
      * OSX 10.10 Yosemite and 10.11 El Crapitan. Only El Crapitan is tested and somewhat supported in case of trouble.
      
      
      * On Linux i will no longer provide mex files for 32-Bit Octave for Intel machines for direct download from us. However, NeuroDebian / Debian upstream / Ubuntu upstream will continue to provide these mex files in a convenient fashion in their "app-stores", so this is not really a drawback, just something to be aware of.

     [Download link for zip file for 3.0.12.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.12.zip)

`Psychtoolbox-3.0.11`
   : [A snapshot of the code as of September 2014: This was the final 3.0.11 release
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
     releases use and require GStreamer-1.0 or later for multi-media functionality.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/Psychtoolbox-3.0.11)

     [Download link for zip file for 3.0.11.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.11.zip)

`Psychtoolbox-3.0.10`
   : [A snapshot of the code as of July 2013: This was the final 3.0.10 release
     before start of the 3.0.11 series. It was the last version that supported
     32-Bit Matlab on OSX.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/Psychtoolbox-3.0.10)

     [Download link for zip file for 3.0.10.](https://github.com/Psychtoolbox-3/Psychtoolbox-3/archive/refs/heads/Psychtoolbox-3.0.10.zip)

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
