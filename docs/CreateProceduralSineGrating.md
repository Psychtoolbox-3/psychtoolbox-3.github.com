# [CreateProceduralSineGrating](CreateProceduralSineGrating)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[gratingid, gratingrect] = [CreateProceduralSineGrating](CreateProceduralSineGrating)(windowPtr, width, height [, backgroundColorOffset =(0,0,0,0)] [, radius=inf][, contrastPreMultiplicator=1])  
  
Creates a procedural texture that allows to draw sine grating stimulus patches  
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
  
### A typical invocation to draw a grating patch looks like this:  
  
[Screen](Screen)('DrawTexture', windowPtr, gratingid, [], dstRect, Angle, [], [],  
modulateColor, [], [], [phase+180, freq, contrast, 0]);  
  
Draws the grating 'gratingid' into window 'windowPtr', at position 'dstRect'  
or in the center if dstRect is set to []. Make sure 'dstRect' has the  
size of 'gratingrect' to avoid spatial distortions! You could do, e.g.,  
dstRect = [OffsetRect](OffsetRect)(gratingrect, xc, yc) to place the grating centered at  
screen position (xc,yc). 'Angle' is the optional orientation angle,  
default is zero degrees. 'modulateColor' is the base color of the grating  
patch - it defaults to white, ie. the grating has only luminance, but no  
color. If you'd set it to [255 0 0] you'd get a reddish grating. 'phase' is  
the phase of the grating in degrees, 'freq' is its spatial frequency in  
cycles per pixel, 'contrast' is the contrast of your grating.  
  
For a zero degrees grating:  
g(x,y) = modulatecolor \* contrast \* contrastPreMultiplicator \* sin(x\*2\*pi\*freq + phase) + Offset.  
  
Make sure to use the [Screen](Screen)('DrawTextures', ...); function properly to  
draw many different gratings simultaneously - this is much faster!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSineGrating.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSineGrating.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralSineGrating.m</code>
</div>

