---
layout: post
title: PTB BETA "Bring in the cat! (+SP5)" released
categories: news
author: kleinerm
---

The new BETA "Bring in the cat!" and its Service Pack 2-5 update was released at 14th May 2016.

As usual, the complete development history can be found in our GitHub repository. The release tag is “PTB_Beta-2016-05-14_V3.0.12”, with the full tree and commit logs under the URL:

Release: <https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2016-05-14_V3.0.12>

### New features:

- TurnTableDemo: Fix for compatibility with Matlab R2015b and later.
- BitsPlusPlus: Add new subfunction 'UseFE1StereoGoggles' to automatically drive those CRS goggles.
- BitsStereoDemo: Make use of modern PTB features like UseFE1StereoGoggles.
- Some file permission cleanups by Yaroslav.
- Fixed some typo in ComputeCIEConeFundamentals() help text by git user spitschan.
- Screen('DrawTextures') speed improvements, only for 64-Bit Screen for Matlab and Octave on Linux for now.
- Screen, PsychHID for RaspberryPi updated.
- XOrgConfCreator now can also setup xf86-video-modesetting, the generic video driver for Linux.
- PsychGPUControl now can deal with Compiz single-x-screen multi-display setups for Ubuntu's standard "Unity" GUI.
- rpath fixes for mex files on Octave-3/4 for 64-Bit OSX to make PTB for Octave on OSX work with different Octave versions.
- VC4 DRI3/Present Mesa 11.2 workaround for Screen() on RaspberryPi.
- Allow normal users PTB low-level access to modern AMD gpu's, e.g., the R9 380 Tahiti Pro.
- Additional performance improvements to Screen('AsyncFlipBegin/End/...') - So far only for 64-Bit Linux.
- Performance improvements to PsychProPixx.
- KDE-5 multi-x-screen "pointer gets stuck" workaround for KDE-5 Plasma on KUbuntu 16.04.0-LTS.
- Minor fixes and improvements to various M-Files.
