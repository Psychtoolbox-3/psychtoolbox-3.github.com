# [CreateProceduralSquareWaveGrating](CreateProceduralSquareWaveGrating)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[gratingid, gratingrect] = [CreateProceduralSquareWaveGrating](CreateProceduralSquareWaveGrating)(windowPtr, width, height [, backgroundColorOffset =(0,0,0,0)] [, radius=inf][, contrastPreMultiplicator=1])  
  
Creates a procedural texture that allows to draw square wave grating stimulus patches  
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
  
'radius' Optional parameter. If specified, a circular aperture of  
'radius' pixels is applied to the grating. By default, no aperture is  
applied.  
  
'contrastPreMultiplicator' Optional, defaults to 1. This value is  
multiplied as a scaling factor to the requested contrast value. If you  
specify contrastPreMultiplicator = 0.5 then the per grating 'contrast'  
value will correspond to what practitioners of the field usually  
understand to be the contrast value of a grating.  
  
The function returns a procedural texture handle 'gratingid' that you can  
pass to the [Screen](Screen)('DrawTexture(s)', windowPtr, gratingid, ...) functions  
like any other texture handle. The 'gratingrect' is a rectangle which  
describes the size of the support.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSquareWaveGrating.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSquareWaveGrating.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralSquareWaveGrating.m</code>
</div>

