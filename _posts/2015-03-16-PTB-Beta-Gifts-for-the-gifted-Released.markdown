---
layout: post
title: PTB BETA "Gifts for the gifted" released
categories: news
author: kleinerm
---

The new BETA "Gifts for the gifted" was relased at 16th March 2015.

As usual, the complete develoment history can be found in our GitHub
repository. The release tag is "PTB_Beta-2015-03-16_V3.0.12", with the
full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-03-16_V3.0.12>

### Major new features and improvements:

-   Experimental Wayland backend for Linux - disabled at compile time.
    Used for development and testing of Wayland 1.7/Weston 1.7, useable
    on those setups for simple tasks, but not ready for prime-time.

-   Many videocapture improvements for increased robustness on certain
    cameras, and for handling USB-3 USBVision IIDC compliant cameras,
    especially tested with PointGrey Flea, and for handling custom
    GStreamer sources like network streaming IP cameras.

-   Initial enablement work for using tracker plugins also under GStreamer.

-   ProPixx fast 4x / 12x mode, initial experimental support.

-   Many cleanups, small improvements and bug fixes.

-   Linux/X11 specific ddx video driver for nouveau dropped, as it
    is now part of the Ubuntu 14.04.2-LTS hardware enablement stack,
    so we don't need our own binary anymore.

-   Linux/X11 specific ddx video driver for intel on XOrg 1.15
    dropped, as Ubuntu 14.04.2-LTS HWE ships with XOrg 1.16 like
    Ubuntu 14.10, so we only need one driver for XOrg 1.16 on both
    14.04.2-LTS and 14.10

-   Imaging pipeline compatibility fixes for Intel gpus. Avoid creating
    FBO's with RGB > 8 bpc color attachments, as Intel HD series can't
    handle those.

-   JavaSwingCleanup() cleanup code improved to make Matlab R2014b
    happy.

-   Retina support improved to also handle windowed windows, not only
    fullscreen on OSX.

-   VBLSyncTest improved to avoid/reduce effects of clock skew with
    Datapixx, new PerceptualVBLSyncTestFlipInfo2.

-   PsychHID on Linux can blacklist more non-keyboards automatically.

-   PsychHID on OSX may be more robust wrt. keyboard queues.

-   Additional pageflipping checks for AMD graphics cards under Linux
    and on OSX with PsychtoolboxKernelDriver.
