# [kPsychNeedHalfHeightWindow](kPsychNeedHalfHeightWindow)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedHalfHeightWindow  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to request use of half-height windows. These  
onscreen windows are treated by all drawing functions (and geometry query  
functions like [Screen](Screen)('Rect', window); or [Screen](Screen)('WindowSize', window);  
as if they only have half the height in pixels. This is a trick to handle  
line interleaved stereo modes or other special display modes, where useable  
vertical drawing area is only half the physical monitor resolution.  
  
Usually user scripts won't pass this flag, but only special setup routines  
that are part of the Psychtoolbox itself.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfHeightWindow.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfHeightWindow.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedHalfHeightWindow.m</code>
</div>

