---
layout: post
title: PTB beta “Arrested Development” released 11.01.2010, Mario takes a break from development
category: news
author: kleinerm
---

### Mario takes a break

The first PTB beta update for 2010, codename “Arrested Development” has
been released 1 week ago. “Arrested Development” is not only the name of
a medical condition, a hip-hop band and a tv series, but also the only
item on my todo-list for Psychtoolbox throughout the next few months. I
have to get the writeup of my thesis finished and time spent on PTB
development & support is a major obstacle to this goal, although a
pleasurable one.

I will continue to monitor the forum for serious problem reports but
only respond to really urgent and important requests, if you make it
really simple for me to help you by preparing your specific questions
carefully according to the guidelines we have at the start page of the
forum and on our Wiki. In short: “Careless emails do not invite careful
responses.” – Other users are of course welcome to help their troubled
colleagues.

A good way to help yourself is to look at the various demo scripts in
the PsychDemos folder if you need help on how to implement certain
things or get examples for coding, to use google to search the forum for
previous answers for similar questions, to search the Wiki for
information, to actually read and follow the instructions for beginners
that our installers print after each single installation and update. It
also helps to actually read error messages and warnings and follow the
pointers to troubleshooting instructions that they quite often contain,
instead of simply copy & pasting them to the forum – Although copying
the output is still better than simply writing “It doesn’t work” in the
most fuzzy way possible.

I’m not interested in discussing feature requests for the next months,
we have a page on our Wiki where you can write those down, together with
a contact address, and i’ll likely come back to you, once i have time to
pick up development again. You are still welcome to submit improved code
or new functionality to me or the other developers for inclusion into
the toolbox, as long as you’re doing most of the work and not me.

I’m also not interested in bug reports for trivial bugs or pure
annoyances. If it is trivial enough for you to fix it yourself, fix it
and send me the updated files. If it is non-trivial for you to fix,
write a bug report and add it to our bug reporting system,
<http://developer.berlios.de/bugs/?group_id=5064> or to the proper
section of our Wiki.

Reports for really serious bugs will still catch my attention if they
are well written and i will do beta updates to fix such bugs should this
become neccessary.

Thanks for your sympathy.

### New features in “Arrested Development”:

These are the new features and improvements of the latest beta. I’ll
post more details when i have time.

-   Good support for international character set handling, Unicode and
    Multibyte/UTF-8 text encoding and other non-ASCII scripts on all
    operating system platforms. Read `help DrawTextEncodingLocaleSettings`
    for further details, as well as the updated help of `Screen
    TextBounds?` and `Screen DrawText?`

-   High-Quality text rendering support with anti-aliasing and Unicode
    drawing on GNU/Linux via use of dynamically loaded FTGL text
    rendering plugin. Should work out of the box. For interesting
    options and troubleshooting if it doesn’t, read `help DrawTextPlugin`.

-   Support for control of power-management and dithering of modern ATI
    GPU’s via `PsychGPUControl()` + proper helper binary executables for
    Windows and Linux. This will require further explanations, stay
    tuned…

-   Workarounds in `IOPort` for broken USB serial drivers as reported by
    Xiangrui Li, see message 10537.

-   Improvements to `PsychRTBox` driver to expose new functionality in
    the latest generation of the `RTBox` response time box.

-   `DaqDIn` may be able to read from USB 1024-LS now, as requested by
    Thomas G. Fikes, see message 10484.

-   Improvements in visual stimulus onset scheduling, realtime
    scheduling and high-precision visual stimulus onset timestamping on
    all platforms as result of the extensive benchmarking and tuning
    efforts on all supported platforms. This will need further
    explanation in the future. If you want to take advantage of it and
    get best possible stimulus onset timing, make proper use of the
    ‘when’ parameter of `Screen('Flip')` and the returned timestamps, as
    explained in the Intro-PDF and demonstrated in a few of our demos.

-   `Kbcheck, KbWait, KbQueueXXX` et al. functions on `MacOS/X` can now
    also handle keypads, not only keyboards. Read their help texts for
    explanation. This code contributed by Roger Woods. Thanks!

-   Initial support for the `VPixx` Technologies `"DataPixx` data
    acquisition and graphics system for the vision sciences". This is
    the first iteration, so far only on OS/X on Intel Macs under
    `GNU/Octave` is supported. This is work in progress. The basic
    infrastructure for good integration into PTB is implemented, tested
    and shown to work very well. As most of the remaining development
    work will be done by VPixx, e.g., support for all other operating
    system platforms and Matlab, i’ll probably do some beta release with
    an update, once all other platforms are ready. See
    `help PsychImaging` and search for Datapixx for supported high
    precision display video modes of the device. Most of our demos for
    high precision stimulus display have been updated to support the
    device as well. help `PsychDataPixx` for more interesting features.
    Again, this is work in progress, a somewhat functional sneak
    preview, not the final product.

-   Some improvements by David Brainard et al. to the `PsychCal`
    subroutines for monitor calibration and similar tasks.

-   Lots of bugfixes, small improvements.

Have fun and good luck, -mario
