# [VideoMultiCameraCaptureDemo](VideoMultiCameraCaptureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Demonstrate simple use of built-in video capture engine.  
  
[VideoMultiCameraCaptureDemo](VideoMultiCameraCaptureDemo)([deviceIds=all][, syncmode=0][, movieName])  
  
[VideoMultiCameraCaptureDemo](VideoMultiCameraCaptureDemo) captures simultaneously from all cameras  
connected to your computer, or a subset of cameras if it is specified  
in the optional vector 'deviceIds', and then shows their video feeds  
in individual Psychtoolbox windows.  
  
The optional 'syncmode' flag allows to select synchronization strategy  
for multi-cam capture: 0 = None, all free-running. 4 = Software sync,  
8 = Firewire Bus-Sync, 16 = Hardware (TTL) trigger sync.  
  
The optional 'movieName' string, if provided, will enable video recording  
of each cameras video into a dedicated movie file, which consists of the  
movieName and a unique camera number.  
  
By default, a capture rate of 30 frames per second at a resolution of  
640 x 480 pixels is requested, and the timecode and interframe interval  
of each captured image is displayed in the top-left corner of each window.  
A press of the [ESCape](ESCape) key ends the demo. The demo also ends automatically  
after a timeout of 10 minutes is reached.  
  
This demo has various hard-coded parameters which allow you to tinker with  
things like Bayer filtering on the camera, versus on the host cpu, versus  
offline later on during playback of recorded video, to select different  
tradeoffs between quality, cpu load, speed and bus bandwidth use. It also  
allows to play with high bit depth (\> 8 bpc) color and luminance formats,  
lossless video recording and other bits and pieces. Change the variables  
as you see fit and read the source carefully.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/VideoMultiCameraCaptureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/VideoMultiCameraCaptureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/VideoMultiCameraCaptureDemo.m</code>
</div>

