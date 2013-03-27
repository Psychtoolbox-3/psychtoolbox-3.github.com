---
layout: post
title: PTB beta “Dancersizing, Grey & Hopeless” release 2012-11-11
category: news
author: kleinerm
---

[Psychtoolbox-3/Psychtoolbox-3@9b5c6901][commit] at [GitHub](https://github.com/Psychtoolbox-3/Psychtoolbox-3)
tag: `PTB_Beta-3.0.10.20121111`

This is mostly a bug-fix release, but it also improves `GetChar` support on
some platforms.

Release Highlights:
-------------------

All systems:
------------

* `GetChar`, `CharAvail`, `FlushEvents` and `ListenChar` now (ab)use keyboard
  queue functionality on setups where use of Java based GetChar et al. is
  ineffective or impossible: This should enable useable support for Windows
  Vista, Windows-7, Windows-8 (untested), Matlab in `-nojvm` mode, and for
  GNU/Octave in its standard terminal command line interface mode, and the GUI
  which will be part of the next major Octave release. Now this mode will use
  keyboard queue functionality, which means it doesn't work if your code
  already makes use of keyboard queues. More specifically: On Linux it will
  block access to the keyboard queue of the default keyboard, all other queues
  will work. On Windows it will block access to all keyboard queues, but allow
  use of the “keyboard queues” to query mice, joysticks and other non-keyboard
  devices. On OSX it will block all use of keyboard queues, because there is
  only 1 queue, as opposed to Linux/Windows which can have many parallel
  queues. Otoh, code that explicitely uses keyboard queues will have a more
  flexible and powerful interface to keyboards anyway. GetChar et al. are just
  for simple and convenient keyboard access, and mostly to keep old code
  working, so this shouldn't be much of a limitation.

* CRS OptiCal support by Andreas Widmann, Uni Leipzig. The `OptiCal()` function
  allows reading measurements from a CRS OptiCAL luminance meter connecte to a
  serial port.

* Various other small improvements.

* PsychPortAudio: Now reports `ElapsedOutSamples` more precise, even in some
  corner-cases where that count could be off by up to a millisecond in the
  past.

* Some audio demos have been improved, ie., cleaned up, to show best practices
  for the current driver instead of the stuff that was considered optimal 2
  years ago. The old code of course still works perfectly with the current
  driver, but sometimes did unneccessary complex stuff that is no longer needed
  for the current driver. `PsychPortAudioTimingTest` now also adapts a bit better
  to the kind of large latencies required to make shoddy MS-Windows setups
  work.

* IOPort: If async background data reception is used, e.g., to automatically
  receive and timestamp trigger bytes from a serial port, and a read timeout
  occurs, e.g., the trigger source hasn't been started within the max 25 secs
  timeout, then the driver will return an empty `[]` packet, instead of one that
  is filled with zeros. The old behaviour was confusing, this one now behaves
  in async mode as it would behave in sync mode.

Linux:
------

* `PsychGPUControl`: Can now also automatically disable 3D desktop composition
  on Ubuntu Linux 12.10, at least when the Unity interface is active. So far it
  was incompatible with 12.10 and did nothing. However, the general
  recommendation is still to manually disable any kind of 3D desktop compositor
  on experiment machines, regardless what OS you use. It avoids possible
  confusion if the automatic fails - which can happen on both Linux and Windows
  under some circumstances without PTB noticing this, and helps performance in
  any case, because even a compositor on standby will use more valuable
  graphics resources and cpu/memory than a disabled compositor.

OSX:
----

* Screen: Videocapture should now also work with 64-Bit Octave on OSX, not only
  with Matlab.

[commit]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/commit/9b5c690196bb818107414eba2fa96f3be2170dd7
