# [CreateProceduralSmoothedDisc](CreateProceduralSmoothedDisc)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[discid, discrect] = [CreateProceduralSmoothedDisc](CreateProceduralSmoothedDisc)(windowPtr, width, height   
[, backgroundColorOffset =(0,0,0,0)] [, radius=inf] [, sigma=11] [,useAlpha=1] [,method=1])  
  
Creates a procedural texture that allows to draw smoothed discs  
in a very fast and efficient manner on modern graphics hardware.  
  
'windowPtr' A handle to the onscreen window.  
  
'width' x 'height' The maximum size (in pixels) of the grating. More  
precise, the size of the mathematical support of the grating. Providing too  
small values here would 'cut off' peripheral parts or your grating. Too big  
values don't hurt wrt. correctness or accuracy, they just hurt  
performance, ie. drawing speed. Use a reasonable size for your purpose.  
  
'backgroundColorOffset' Optional, defaults to [0 0 0 0]. A RGBA offset  
color to add to the final RGBA colors of the drawn grating, prior to  
drawing it.  
  
'radius' If specified, a circular aperture of  
'radius' pixels is applied to the grating. By default, aperture == width.  
  
'sigma' edge smoothing value in pixels  
  
'useAlpha' whether to use colour (0) or alpha (1) for smoothing channel  
  
'method' whether to use cosine (0) or smoothstep (1) functions. If you  
 pass (2) then the smoothstep will be inverted, so you can use it as a  
 mask (see [ProceduralSmoothedDiscMaskDemo](ProceduralSmoothedDiscMaskDemo).m for example).  
  
The function returns a procedural texture handle that you can  
pass to the [Screen](Screen)('DrawTexture(s)', windowPtr, id, ...) functions  
like any other texture handle. The 'discrect' is a rectangle which  
describes the size of the support.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedDisc.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedDisc.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedDisc.m</code>
</div>

