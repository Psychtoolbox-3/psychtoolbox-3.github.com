---
layout: post
title: PTB BETA "Tediousness overdrive" released
categories: news
author: kleinerm
---

The new BETA "Tediousness overdrive" was relased at 25th July 2015.

As usual, the complete develoment history can be found in our GitHub
repository. The release tag is "PTB_Beta-2015-07-25_V3.0.12", with the
full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-07-25_V3.0.12>

### New features and improvements:

- KbWait: Fix treatment of empty forWhat argument.
- Screen: Fix PTB-2 emulation mode a bit.
- Screen/Linux: Dis/Enable DPMS while onscreen windows are open.
- Screen/Linux: Detect use of DRI3/Present.
- Screen/OSX: Fix color handling of OS X native text renderer.
- Improve help text of GetGamepad/Keyboard/KeypadIndices
- Add Screen('DrawText') color precision test case to HighColorPrecisionDrawingTest.
- DrawFormattedText: Improve bounding box precision for single-line case.
- DaqAInScan: Make it potentially a bit faster for USB 1608-FS.
- Screen/OSX: Remove hybrid graphics workaround for MBP 2010
- DaqALoadQueue: More fixes for Octave compatibility and basic sanity.
- Screen/Linux: Use old-style override_redirect on  multi-x-screen KDE.
- Screen/Linux/X11: Prevent crash at Screen reload on multi-x-screen with buggy Mesa.
- Screen/Linux/X11: Restrict workaround for Mesa mapi bug to Mesa < 10.5.2
- White-list Mesa versions >= 10.5.9 and >= 10.6.2 for XCloseDisplay()
- NetStation: Improve and consolidate various improvements. - Gergely Csibra
- Screen: Add new optional 'ignoreErrors' flag to 'LoadNormalizedGammaTable'
- Screen: Make FTGL plugin the default text renderer on OSX.
- BasicSoundScheduleDemo: Remove redundant 'RunMode' 1 assignment.
- Screen/OSX: Try to make modesetting Retina compatible.
- VideoCaptureDemo, VideoDelayLoopMiniDemo: Use default ROI by default.
- Snd(): Some fixes for corner use case.
- PsychVideoDelayLoop: Cleanup textures at end of each session.
- Update "help DrawTextPlugin" for new default FTGL renderer on OSX.
- Screen: Improve Screen('Close', window);
- Screen/OSX: Fix cursor movement lag after SetMouse()
- Screen/OSX: Return OS reported mouse delta movement in GetMouse() valuators.
- Screen: Add 'detachFromMouse' support to SetMouse().
- Screen: Fix CopyWindow to use windows clientRect instead of rect for Retina/HiDPI compatibility
- Screen/OSX: Fix hostname display in Screen('Computer')
- DrawFormattedText: Remove 250 chars linebreak on OSX. - Diederick Niehorster
- Screen: CopyWindow update help text.
- Screen/Linux: Make ext_buffer_age warning less chatty.
- Speak: Fix use with apostrophes in text string. - elladawu
- ImageUndistortionDemo: Minor improvements.
- ImagingVideoCaptureDemo: Add a (disabled) test line for CSV geometrycorrection.
- CreateDisplayWarp: Bug fix and enhancement for CSV method.
- New prototype quality display correction method: DisplayUndistortionLabRiggerMouseStim.m
- PsychImaging: Update help text for task 'UseRetinaResolution'
- Update and extend conversions between degrees and mm of retina - David Brainard.
