# [ApriltagsDemo](ApriltagsDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ApriltagsDemo](ApriltagsDemo)([camId][, colordepth=1][, tagSize=0.017][, tagFamily='tag16h5'][, targetMarkers])  
  
Use [ApriltagsDemo](ApriltagsDemo) to track April tag markers and visualize them in live-video.  
  
Minimalistic demo on how to capture video data and use PsychCV's builtin  
apriltag marker tracking to detect and track the rigid position and orientation  
of such fiducial markers, then visualize corresponding 3D objects on top of the  
live video of the markers via [OpenGL](OpenGL).  
  
Note that this demo can only act as a starting point. There are too many parameters  
which need to be set for your specific use case, and we can't pass all of them via  
function parameters. Read the code, think about it, hack it accordingly.  
  
### Optional parameters:  
  
camId = Id of the camera to use, [] selects default cam.  
colordepth = Video capture mode: 1 = Mono/Gray, 3 = RGB color, 4 = RGBA color.  
tagSize = Size of April tag (edge length) in meters. Needed for 3D pose estimation.  
tagFamily = April tag family to use.  
targetMarkers = List of marker id's to track and return. Default is [] for "all markers".  
  
  
Press any key to finish the demo.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ApriltagsDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ApriltagsDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ApriltagsDemo.m</code>
</div>

