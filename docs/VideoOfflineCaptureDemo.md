# [VideoOfflineCaptureDemo](VideoOfflineCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate use of built-in [[GStreamer](GStreamer)][(GStreamer)]((GStreamer)) video capture engine to capture first  
into memory, then retrieve corresponding video textures after end of capture.  
  
[VideoOfflineCaptureDemo](VideoOfflineCaptureDemo)([fullscreen=0][, fullsize=0][, roi=[0 0 640 480]][,deviceId=0])  
  
[VideoOfflineCaptureDemo](VideoOfflineCaptureDemo) initializes the first attached and supported camera on  
your computer (e.g, the built-in iSight of Apple Macintosh computers),  
then records video from it into memory until you press a key. It then  
fetches and displays all previously recorded images, then quits. Abort  
display by pressing any key on the keyboard.  
  
By default, the maximum supported framerate is requested and the  
timecode and interframe interval of each captured image is displayed in  
the top-left corner of the display.  
  
See also [ImagingVideoCaptureDemo](ImagingVideoCaptureDemo), [VideoDelayloopMiniDemo](VideoDelayloopMiniDemo) and a few other  
nice demos.  
  
### Optional parameters:  
  
'fullscreen' If set to non-zero value, the image is displayed in a  
fullscreen window, as usual, otherwise a normal GUI window is used.  
  
'fullsize' If set to 1, the cameras image is scaled up to full screen  
resolution, ie. so it fills the maximum amount of display area, but  
preserving the original aspect ratio.  
  
'roi' Selects a rectangular subregion of the camera for display. By  
default, it selects a [0 0 640 480] rectangle, ie. the full are of a  
camera with 640 x 480 pixels resolution. This parameter may need tweaking  
for some cameras, as some drivers have bugs and don't work well with all  
settings.  
  
'deviceId' Device index of video capture device. Defaults to system default.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoOfflineCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoOfflineCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoOfflineCaptureDemo.m</code>
</div>

