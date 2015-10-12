---
layout: post
title: PTB BETA "Immersator" SP2 released
categories: news
author: kleinerm
---

The new BETA "Immersator" SP2 was released at 12th October 2015.

As usual, the complete develoment history can be found in our GitHub repository. The release tag is “PTB_Beta-2015-10-12_V3.0.12”, with the full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-10-12_V3.0.12>

From now on, OSX versions before 10.11 El Capitan are no longer tested or officially supported.
OSX 10.8 - 10.10 should continue to work, but no problems relating to these versions will be
handled and no bugs will be fixed. Only OSX 10.11 El Capitan will receive basic testing, bug
fixes and support.

### New features and improvements:

- Allow H264 profile selection for movie writing. Demo this in ImagingStereoDemo by choosing Profile=2, the "Main Profile", something that even works with deficient movie players like Apples Quicktime.

- Fixes for El Capitan, Apples latest goddamn awful "masterpiece".

   - No longer completely hang and deadlock Octave-3/4 in GUI mode due to El Capitan bugs.
   - Avoid initial sync failure, caused by new El Capitan bugs, via some dirty hack.
   - Reduce frequency of white flashes when there shouldn't be any, caused by El Capitan bugs. Dirty hack.
   - Make frozen/black screen hangs at end of a session slightly less frequent via a new hack.
   - Auto fallback from stereomode 1 to stereomode 11 on OSX if mode 1 is unsupported, as is the case on El Capitan, where Apple decided that their users do no longer need professional stereo display support.
   - Rebuilt all OSX mex files against XCode 7 and OSX 10.11 SDK's.
   - Change support status on OSX: 10.11 El Capitan now supported, support for OSX 10.10 Yosemite cancelled.
