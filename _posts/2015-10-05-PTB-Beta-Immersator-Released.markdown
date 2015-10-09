---
layout: post
title: PTB BETA "Immersator (+SP1)" released
categories: news
author: kleinerm
---

The new BETA "Immersator" and its SP1 were relased at 5th October 2015.

### New features and improvements:

#### Highlights:

- General Virtual Reality HMD support infrastructure, with a driver specifically for the Oculus Rift DK1 and DK2.

  Look at "help OculusVR" and "help PsychVRHMD" for general setup and usage instructions.
  
  Look at the demos MovingLineDemo, VRHMDDemo, VRHMDDemo1, SuperShapeDemo, ImagingStereoDemo(103), MorphDemo on how to use this.

#### General improvements:

- Support for use with 64-Bit Octave-4 on OSX via HomeBrew.
- HighColorPrecisionDrawingTest: Robustness improvements to deal with the latest brokenness of OSX 10.11
- Eyelink: Optionally prevent opening of existing EDF files to protect against accidental overwriting of data files.
- LoadGLSLProgramFromFiles/LoadShader: Improve debugging output. Contributed by Diederick.
- ImagingStereoDemo and others: Compatibility fixes for Matlab R2014a
- KbQueueReserve: Check for invalid deviceIndex with more than one element.
- GetMouseIndices: Add option 'slavePointers' for simpler use of KbQueues with mice on Linux.
- Fixes and improvements to Quest by Denis Pelli.
- Some small fixups for HomeBrew, and VRHMDDemo1.m
