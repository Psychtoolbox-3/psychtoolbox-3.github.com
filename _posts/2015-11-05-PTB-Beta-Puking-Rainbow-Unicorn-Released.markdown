---
layout: post
title: PTB BETA "Puking Rainbow Unicorn" released
categories: news
author: kleinerm
---

The new BETA "Puking Rainbow Unicorn" was released at 5th November 2015.

As usual, the complete develoment history can be found in our GitHub repository. The release tag is “PTB_Beta-2015-11-05_V3.0.12”, with the full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-11-05_V3.0.12>

### New features and improvements:

- Introducing 32-Bit Octave-4 support for MS-Windows. Psychtoolbox should now work with 32-Bit Octave-4.0.0
  as provided by the following official MXE Setup.exe installer provided by the Octave developers:

  <http://wiki.octave.org/Octave_for_Microsoft_Windows#Octave-4.0.0>

  Light testing shows that Psychtoolbox should work well with Octave-4 for Windows, except for video capture
  and video recording. Trying to use video capture will cause an immediate termination of Octave for currently
  unknown reasons. 32-Bit Octave-4 is only supported because the Octave upstream developers currently do not provide a
  64-Bit build and installer for Octave. As soon as upstream would provide a 64-Bit Octave-4 installer, we would
  immediately switch to 64-Bit Octave support and cancel support for 32-Bit Octave, so do not rely on
  reintroduced 32-Bit support being around for too long on Windows.

- Experimental NVidia USB NVision emitter/stereo goggles support for 64-Bit Linux. This is untested due to lack
  of suitable hardware so far. It should allow to use any graphics card under Linux in frame sequential
  stereo mode with such NVidia stereo goggles, driven via the USB connection.

- AMD Volcanic Islands gpu family low-level support for Linux and OSX. This covers the latest graphics cards
  from AMD.

- Auto-detection of display head assignments for Linux and OSX on AMD gpus. Instead of using a heuristic, as
  for NVidia gpus, this should automatically find the correct setup for AMD gpus. A side effect of the auto-
  detection is a short flicker of all displays when the Screen mex file gets loaded on OSX or when the first
  onscreen window opens on Linux.

- XOrgConfCreator + XOrgConfSelector assistants for Linux: XOrgConfCreator is a little setup assistant that
  automatically creates a xorg.conf display server configuration file by looking at the systems display setup
  and asking a few questions to the user. This should simplify setup of high performance multi-display setups
  on Linux. XOrgConfSelector allows to easily apply such config files on the given setup, switching between
  multiple different configs depending on experimental needs or regular desktop use.

- PsychLinuxConfiguration improvements for Linux. New tweaks for performance tuning.

- Screen('DrawDots') shader based smooth point rendering support. On graphics drivers which don't support
  drawing of smooth dots this will implement smooth dots via use of a GLSL shader. Use of shader based
  drawing of smooth dots can also be triggered via the new 'dot_type' flags 3 and 4. Using shader based
  dot drawing can be useful to enhance drawing performance on all gpu's if one wants to draw lots of dots
  of variable size, as the GLSL shader based drawing code can draw dots of varying size faster than the
  standard code by use of some special shader features.

- Improvements to Shuffle(), contributed by GitHub user NxNiki.

- Add new kPsychGfxCapVCGood flag for ConserveVRAM settings to work around gpu texture sampling precision issues on some gpus
  with some graphics drivers, e.g., AMD gpus on OSX 10.11. You can use HighColorPrecisionDrawingTest with
  test blocks 3, 4 and 5 to test for these problems. The test will tell you to use this flag as one measure
  to improve precision if needed.

- Add HiDPI detection code for MS-Windows, with hopefully useful troubleshooting messages. On Windows-7 and
  earlier Windows versions, Psychtoolbox can prevent timing issues caused by HiDPI/Retina high pixel density
  displays by disabling the DWM desktop compositor for fullscreen onscreen windows. On Windows-8 and later,
  PTB can't prevent such issues, so it has to rely on the given Matlab or Octave host application being DPI
  aware, so MS-Windows does not need to enable DWM based DPI virtualization and rescaling. PTB can now detect
  problematic behaviour of Matlab and provide some hints on how to avoid DPI related trouble, but it can't
  fix it, as that is not technically possible on MS-Windows.

- PR655Init() tweaks for improved robustness on OSX.

- Various bug fixes and minor improvements in various places.
