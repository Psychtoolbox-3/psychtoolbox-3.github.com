# [ARToolkitDemo](ARToolkitDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

Use [ARToolkit](ARToolkit) to track and visualize 3D objects in live-video.  
  
Usage: [ARToolkitDemo](ARToolkitDemo)([multiMarker = 2])  
  
Minimalistic demo on how to capture video data and use [ARToolkit](ARToolkit) to  
detect and track the rigid position and orientation of markers, then  
visualize corresponding 3D objects on top of video via [OpenGL](OpenGL).  
  
Please note that [ARToolkit](ARToolkit) is only supported when running Psychtoolbox  
under GNU/Octave, not when using it with Matlab. Therefore this demo  
won't work with Matlab.  
  
### Parameters:  
  
multiMarker = If set to 2 (default), track single markers. If set to 1,  
track so called multi markers or composite markers for more robustness  
against occlusion of single markers. A setting of 3 (=1+2) should track  
both types of markers simultaneously, but this doesn't seem to work well  
yet.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ARToolkitDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ARToolkitDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ARToolkitDemo.m</code>
</div>

