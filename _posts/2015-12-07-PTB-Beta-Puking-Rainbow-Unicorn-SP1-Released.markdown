---
layout: post
title: PTB BETA "Puking Rainbow Unicorn SP1" released
categories: news
author: kleinerm
---

The new BETA "Puking Rainbow Unicorn SP1" was released at 7th December 2015.

As usual, the complete develoment history can be found in our GitHub repository. The release tag is “PTB_Beta-2015-12-07_V3.0.12”, with the full tree and commit logs under the URL:

<https://github.com/Psychtoolbox-3/Psychtoolbox-3/tree/PTB_Beta-2015-12-07_V3.0.12>

### New features and improvements:

- Fix AMD GPU DCE-8+ display engine handling on Linux and OSX. Latest generation AMD gaphics cards are now fully supported.
- Fix OSX PsychtoolboxKernelDriver multi-display handling bugs introduced by the "Puking Rainbow Unicorn" beta.
- Improve 10 bpc pixelformat selection for OSX for native 10 bit framebuffer support. Untested due to lack of iMac 5k hardware.
- Minor bug fixes and documentation updates in various places.
- OSX: Maybe improve detection and handling of USB-DAQ devices. PsychHID for OSX may now support USB device selection by HID interfaceID,
which might improve robustness of USB-DAQ detection and DaqAInScan functionality. Completely untested due to lack of hardware.
- Windows: Improve visual stimulus timing on Windows-10, and maybe on Windows 8/8.1 (untested). On a Windows-10 test system with a 5 year old
AMD Radeon HD-5770 this makes visual stimulation timing and timestamping work ok, despite the DWM being permanently enabled. More tests are
needed, but this might allow at least basic use of Windows-10.
