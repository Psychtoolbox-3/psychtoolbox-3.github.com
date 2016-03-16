---
layout: post
title: PTB BETA "Nothing but the rain SP1" released
categories: news
author: kleinerm
---

The new BETA "Nothing but the rain" and its Service Pack 1 update was released at 15th March 2016.

As usual, the complete development history can be found in our GitHub repository. The release tag is “PTB_Beta-2016-03-15_V3.0.12”, with the full tree and commit logs under the URL:

Release: <https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2016-02-21_V3.0.12>

SP1:     <https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2016-03-15_V3.0.12>

### New experimental features:

- Basic alpha-quality support for Psychtoolbox on the Raspberry Pi model 2B. This requires the brand-new experimental/alpha-quality open-source OpenGL graphics/display drivers written by Eric Anholt for the Pi's VideoCore-4 gpu on Broadcom's SoC. These drivers are now backported to the February 2016 update of Raspbian, the Debian GNU/Linux variant for Raspberry Pi. This is more of a sneak preview to work in progress than production quality for neuro-science applications atm. See http://anholt.livejournal.com/45752.html for current driver status.

### Text drawing improvements:

- Screen('TextTransform') allows application of a 2D affine transform only to drawn text strings. Currently supported on the standard FTGL drawtext text renderer with high performance and good quality, and on the unsupported/deprecated legacy Apple OSX Coretext text renderer at the cost of a drastic performance loss and almost completely useless Screen('TextBounds') bounding box results. Screen TextTransform? explains some of the gotchas and traps you will run into if you really think you want to use this function.

- Screen('DrawText') now returns more accurate/useful new text cursor position and a new optional 'textHeight' for "newline" vertical spacing. These enhancements only with the standard FTGL drawtext plugin renderer, not on the legacy renderers.

- Support for sub-pixel anti-aliasing ("LCD filtering") on the legacy Apple CoreText renderer 0, if that renderer is manually selected, and 'TextAntialiasing' preference setting 2 is selected and preference 'TextAlphaBlending' is enabled via setting 1 and a solid opaque 'TextBackgroundColor' is selected. Sub-pixel anti-aliasing only works on OSX under those special conditions. In all other cases, only regular per-pixel anti-aliasing is used, as in the past.

- Fix memory leak in legacy OSX CoreText renderer and other OSX text renderer bugs.

- Other small text quality improvements.
    
- "help DrawTextPlugin" Update for latest OSX + Matlab trouble.

### Small improvements:

- Replace 'clear all' in many demos with a more harmless clear; Probably also not great, but better than that other disaster. Also replace some calls to GetChar/CharAvail, as we don't want to give too many bad examples.

- Add option ListenChar(-1): This only disables spilling of typed characters into the Matlab/Octave command window (like ListenChar(2)) but without enabling keyboard listening (GetChar et al.). This allows to use character suppression in parallel to use of Keyboard queues.

- Add replacements psychwavread/psychwavwrite for wavread/wavwrite which were removed in Matlab R2015b. Used in our audio demos to provide a less brain-dead approach to basic backward compatibility than Mathworks.

- Robustness improvements and/or bug fixes and/or help text updates to AutoBrightness, GazeContingentDemo/BubbleDemo, HighColorPrecisionDrawingTest, MeasureDpi, Kbqueues, BitsPlusIdentityClutTest, KbCheck, Screen('CopyWindow'), OSX legacy CoreText renderer, FrameSequentialStereoTest, GetEchoString, GetKbChar, DrawFormattedText, PsychHIDTest...

- Windows: Allow Screen('LoadNormalizedgammatable') to load > 256 slots gamma tables to devices like CRS Bits# or VPixx Datapixx. GPU hw gamma tables are still limited to 256 slots due to OS restrictions.

- GetEchoString and AutoBrightness: Cosmetic and help text fixes.

- XOrgConfCreator: Slightly more robust error handling against broken graphics setups.

- Screen('DrawDots'): Make shader-based path more friendly to gpu drivers.

- Add udev rule for potentially simplified use of Griffin Powermate on Linux.

- Some improvements by the Brainard lab to PsychColorimetric utility routines.
    
- Other small improvements here and there.
