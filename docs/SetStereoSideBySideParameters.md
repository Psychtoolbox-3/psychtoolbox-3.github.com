# [SetStereoSideBySideParameters](SetStereoSideBySideParameters)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

Change parameters for side-by-side stereo display modes (4 and 5).  
  
[SetStereoSideBySideParameters](SetStereoSideBySideParameters)(win [, leftOffset][, leftScale][, rightOffset][, rightScale][, shaders])  
  
Call this function after the win = [PsychImaging](PsychImaging)('OpenWindow',...); call on an  
onscreen window in side-by-side stereo mode to change the parameters  
of drawing the stereo views.  
  
All parameters except the onscreen 'win'dowhandle are optional and have  
reasonable builtin defaults:  
  
'leftOffset' = Top-Left [x,y] offset of left eye framebuffer in relative  
coordinates [0,0] == top-left of framebuffer, [1,0] == 1 stereo window  
width to the right, [2,0] == 2 stereo window width to the right etc.  
  
'leftScale' = Scaling of left eye image buffer. E.g., [1,1] == Don't  
scale. [0.75, 0.5] scale to 75% of original width, 50% of original  
height.  
  
'rightOffset', 'rightScale' == Ditto for right eye image.  
  
'shaders' a vector containing the GLSL handles of a new pair of shaders to replace  
the standard builtin side-by-side compositing shaders. shaders(1) for left eye  
view, shaders(2) for right eye view. The old shaders are deleted if new shaders  
are assigned.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/SetStereoSideBySideParameters.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/SetStereoSideBySideParameters.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/SetStereoSideBySideParameters.m</code>
</div>

