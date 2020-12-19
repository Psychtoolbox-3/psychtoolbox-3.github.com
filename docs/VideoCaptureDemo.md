# [VideoCaptureDemo](VideoCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate simple use of built-in video capture engine.  
  
[VideoCaptureDemo](VideoCaptureDemo)([fullscreen=0][, fullsize=0][, roi][, depth][, fps=realmax][,deviceId=0][, cameraname][, bpc=8])  
  
[VideoCaptureDemo](VideoCaptureDemo) initializes the first attached and supported camera on  
your computer (e.g, the built-in iSight of Apple Macintosh computers),  
then shows its video image in a Psychtoolbox window.  
  
By default, the maximum capture rate for a given resolution is requested, and the  
timecode and interframe interval of each captured image is displayed in  
the top-left corner of the display. A press of the [ESCape](ESCape) key ends the  
demo.  
  
See also [ImagingVideoCaptureDemo](ImagingVideoCaptureDemo), [VideoDelayloopMiniDemo](VideoDelayloopMiniDemo) and a few other  
nice demos.  
  
### Optional parameters:  
  
'fullscreen' If set to non-zero value, the image is displayed in a  
fullscreen window, as usual, otherwise a normal GUI window is used.  
  
'fullsize' If set to 1, the cameras image is scaled up to full screen  
resolution, ie. so it fills the maximum amount of display area, but  
preserving the original aspect ratio.  
  
'roi' Selects a rectangular subregion of the camera for display. By  
default, it selects the full area of the camera, if possible. This  
parameter may need tweaking for some cameras, as some drivers have  
bugs and don't work well with all settings.  
  
'depth' Number of color channels 1 = grayscale, 3 = rgb, 4 = rgba etc.  
  
Tip for the Microsoft Surface Pro 6 tablet and similar: The builtin cameras only  
work if you explicitely specify the 'depth' parameter as value 6 for YUV-I420.  
This seems to be a quirk of the builtin cameras, as of Windows-10 (20H2) from  
December 2020.  
  
'fps' Target capture framerate. Maximum for given resolution and color depth  
if omitted.  
  
'deviceId' Device index of video capture device. Defaults to system default.  
  
Tip on Linux: If you have an exotic camera which only delivers video in non-standard  
video formats, and Psychtoolbox does not handle this automatically, but aborts with  
some [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) errors, e.g., "source crop failed", or "negotiation error", you may  
be able to work around the problem (after a "clear all" or fresh start), by adding  
this command: setenv('GST\_V4L2\_USE\_LIBV4L2','1');  
This will use of a helper library that can convert some video formats which  
[[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) or Psychtoolbox can not handle automatically yet. In any case, please  
report your problem to the Psychtoolbox user forum, so proper automatic handling  
of your camera model can be added to a future Psychtoolbox version.  
  
'cameraname' Name string for selection of video capture device. This is  
only honored if 'deviceId' is a negative number, and only for certain  
video capture plugins. Defaults to none.  
  
'bpc' Optional bit depth in bits per channel. Defaults to classic 8 bpc, but  
some cameras support up to 16 bpc. Setting 16 bpc will try to coerce those into  
providing "HDR" data. Usually this works with higher end firewire cameras and  
the dc1394 capture engine. Your mileage with standard consumer cameras and the  
default [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) capture engine will likely be less great. If at all, it would  
probably only work on Linux or on OSX with [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) built from source, so you  
have the camerabin1 plugin available.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoCaptureDemo.m</code>
</div>

