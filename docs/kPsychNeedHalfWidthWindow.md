# [kPsychNeedHalfWidthWindow](kPsychNeedHalfWidthWindow)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedHalfWidthWindow  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to request use of half-width windows. These  
onscreen windows are treated by all drawing functions (and geometry query  
functions like [Screen](Screen)('Rect', window); or [Screen](Screen)('WindowSize', window);  
as if they only have half the width in pixels. This is a trick to handle  
dual-display stereo modes or special display modes like CRS Color++ mode  
for the Bits++ box, where useable horizontal drawing area is only half  
the physical monitor resolution due to the special image processing  
inside the Bits++ box. Usually user scripts won't pass this flag, but  
only special setup routines that are part of the Psychtoolbox itself.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfWidthWindow.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfWidthWindow.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfWidthWindow.m</code>
</div>

