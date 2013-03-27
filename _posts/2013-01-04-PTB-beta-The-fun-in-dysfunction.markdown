---
layout: post
title: PTB beta “The fun in dysfunction” release 2013-01-04
category: news
author: kleinerm
---

[Psychtoolbox-3/Psychtoolbox-3@89ac3a06][commit] at [GitHub](https://github.com/Psychtoolbox-3/Psychtoolbox-3)
tag: `PTB_Beta-2013-01-04\_V3.0.10`

Release Highlights:
-------------------

All systems:
------------

* Support for GStreamer `camerabin2` video capture & recording: Once a future
  release of the GStreamer-SDK catches up in functionality, this will enable
  video capture and recording on 64-Bit OSX and for 64-Bit Matlab on
  MS-Windows. Currently it only works on Linux, or for 32-Bit Matlab on Windows
  or for OSX either with 32-Bit Matlab or with a self-compiled GStreamer
  installation from Homebrew.

* Support for a new builtin imaging pipeline panel fitter: This allows to open
  onscreen windows whose drawing area size is bigger or smaller than the area
  of the screen occupied by the window. A new optional parameter `clientRect`
  for `Screen('Openwindow',...);` allows to specify the “virtual size” of the
  window, whereas the old `rect` parameter still specifies the true size of the
  window on the screen. Psychtoolbox will pretend your window is only the size
  of `clientRect`, but at `Screen('Flip')` time it will upscale or downscale your
  stimulus image to the true size of the window, applying linear or better
  filtering for this zoom. Why would you want to do that? Typical flat panels
  and projectors only work optimally at their native resolution. All other
  resolutions usually cause at least funny timing problems or sometimes visual
  artifacts with dynamic stimuli. This option allows you to transfer a script
  written for visual stimulation on, e.g., a CRT monitor or a panel on a
  certain resolution, to a different experimental setup which has a different
  native display resolution with minimal modifications to the script in case
  your script made assumptions about the display resolution in use. It would be
  especially useful if you worked in a place where some equipment is badly
  maintained and tends to break down in the middle of data collection, so it
  needs to be swapped with incompatible equipment of different native
  resolution. This release still misses the high-level setup code in
  `PsychImaging()` to access and configure this feature in convenient ways, so
  the panel fitter may not work well or need some tinkering when used together
  with some advanced features, e.g., some stereo display modes or high
  precision display modes which use a unusual display geometry themselves. This
  will be fixed in a future release. For standard bread & butter rescaling it
  works well. Of course it is still better to choose your resolutions wisely or
  write your code resolution independent if possible, as the scaling comes at
  some cost of another millisecond or two spent on rescaling in the gpu.

* Small fixes to PsychKinectCore and to PsychHID.

* Various other fixes for small documentation and PTB bugs.

* Potential multi-threaded decoding improvements for GStreamer movie playback.
  The multi-threaded high performance playback mode introduced in the previous
  beta is so far only effective on Linux and on the GStreamer packages provided
  by the Homebrew package manager on OSX, but not with the GStreamer-SDK on OSX
  or Windows. This beta prepares higher performance playback with a future
  version of the GStreamer-SDK.

* Support for a popular HDMI stereo frame packing format, side-by-side
  horizontally compressed stereo. `PsychImaging()` has a function to enable this,
  `ImagingStereoDemo(102)` demonstrates it.

* Datapixx and Eyelink improvements.

* Use of multisample anti-aliasing MSAA with imaging pipeline enabled should
  now work better on deficient OSX graphics drivers, especially in 3d rendering
  mode due to addition of new/improved error handling and fallback path.

Linux:
------

* Improved Linux support for timestamping, graphics problem detection and
  desktop compositor handling. This further increases the advantage Linux users
  already had over OSX and Windows users wrt. timing precision. This beta has
  been tested with different common desktop GUI's for Linux wrt. to correct
  stimulus display, proper timing and timestamping and display synchronization
  across dual-display setups, e.g., for stereoscopic presentation, with a
  NVidia GeForce 8800 card under Ubuntu Linux 12.04.1-LTS, the latest NVidia
  binary drivers and a Datapixx for external measurement of stimulus onset
  timing and timestamping. It works perfectly well on single-display and on
  dual-display setups under KDE-4 with KWin desktop manager,
  GNOME-3/Gnome-Shell with Mutter dektop manager, LXDE with OpenBox, GNOME-2
  classic without desktop compositor, and XFCE-4 with/without compositor. It
  works perfectly well on single display setups, but not on multi-display
  setups with desktop GUI's based on Compiz: Unity and GNOME-2 work well single
  display but not dual-display. This must be a bug in Compiz introduced by the
  latest software updates to Ubuntu 12.04 LTS sometime December 2012. Canonical
  applied some optimizations to improve video game performance, which worked
  out well on single display setups, but apparently went wrong for dual-display
  setups. It doesn't work well at all with the Unity-2D desktop, something is
  broken there. If you run data collection i would recommend running a desktop
  GUI without compositor, e.g., by creating a separate “experiment” user
  account on your machine where data collection is run and a pure 2d desktop is
  installed, e.g., XFCE-4 with desktop composition turned off, or LXDE+OpenBox.
  This gives you that extra piece of mind that even if there would be
  compositor related bugs in Psychtoolbox or your system, no compositor could
  interfere, because something that doesn't exist can't interfere. It may also
  give you a few percent extra performance. However, the desktop GUIs mentioned
  above are well behaved even if a compositor is active, as PTB can temporarily
  turn off the compositor, or the compositors switch themselves to standby
  during an experiment session. It's a tradeoff you have to make between
  paranoia vs. convenience and bling.

* Improved workarounds for handling of slightly broken Intel-DDX graphics
  drivers on Linux (pre 2.20.16 series). Intel video drivers before version
  2.20.16 but after June 2011 have a bug in their swap scheduling. Psychtoolbox
  will detect this bug and enable a workaround for such drivers since the
  previous beta. The detection code has been improved. Of course it is best to
  update to a fixed driver (v2.20.16 or later) asap.

Windows:
--------

* Improved support for handling of MS-Windows-8 dektop compositor: Psychtoolbox
  is better at detecting if a desktop compositor on Windows Vista/7/8
  interferes with timing and can warn you in most cases. However, Windows-8
  does no longer allow to disable the compositor, neither manually by you, nor
  automatically by us. This means you have to completely rely on the compositor
  disabling itself for fullscreen window displays, something that didn't work
  well at all in the past. Testing with an up to date Windows-7 system showed
  that the compositor now auto-disables for fullscreen windows on
  single-display setups, but fails miserably on multi-display setups. I didn't
  test with Windows-8 as we don't have or use that os. Maybe Windows-8 behaves
  better than Windows-7. If it doesn't then it is completely unuseable for
  timed stimulus presentation an anything but a single display setup, with no
  second monitor even connected.

OSX:
----

* Bugfixes / Workarounds for some MS-Windows bugs and many new MacOSX 10.7+
  operating system bugs. If i had to describe Apples latest operating systems
  in one word it would be “Dysfunctional”. Especially many fixes are related to
  use of high-precision display devices like
  Datapixx/Viewpixx/Propixx/Bits+/Bits\# etc.

[commit]: https://github.com/Psychtoolbox-3/Psychtoolbox-3/commit/89ac3a065cf2d29f6bdc9ee8e90f81e022c710b7 
