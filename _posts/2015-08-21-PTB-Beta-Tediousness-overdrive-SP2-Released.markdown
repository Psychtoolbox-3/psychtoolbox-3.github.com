---
layout: post
title: PTB BETA "Tediousness overdrive SP1/SP2" released
categories: news
author: kleinerm
---

The new BETA "Tediousness overdrive" SP1 and SP2 were relased at 21st August 2015.

### New features and improvements:

- Datapixx on Octave OSX fixes.
- PsychHID robustness improvements in HID device enumeration for OSX. Removes failure of PsychHID if special devices like, e.g., Oculus VR Rift, are connected.
- AutoBrightness fix from Denis. Now probably works on both OSX 10.10 and 10.9.
- QuestUpdate improvement from Denis: Make sure "intensity" is real, not complex.
- DrawFormattedText: Fix bug for Unicode text introduced when improving single-line text centering.
- Some fixes for text drawing provided or suggested by Diederick:
-- Screen: Fix returned alpha value in Text(Background)Color.
--  Screen('DrawText'): Remove the escaping of ampersand from DrawFormattedText()
- Fix Var2Str: failed when infinity imaginary component in variable. Provided by Diederick.
- Unit Tests: make use of capturing exception info in the catch instead of lasterr. By Diederick.
- Fixes and improvements to color handling routines by David.
- OSX mex file fixes for Octave: Drop Octave 3.8.1 support for OSX HomeBrew, add 3.8.2_2 support instead.
- Some new tests and other minor improvements, e.g., to demos.
- New test: DatapixxGPUDitherpatternTest - Test GPU dithering via Datapixx.
