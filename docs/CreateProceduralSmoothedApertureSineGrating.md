# [CreateProceduralSmoothedApertureSineGrating](CreateProceduralSmoothedApertureSineGrating)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[gratingid, gratingrect] = [CreateProceduralSmoothedApertureSineGrating](CreateProceduralSmoothedApertureSineGrating)(windowPtr, width, height [, backgroundColorOffset =(0,0,0,0)] [, radius=inf] [, contrastPreMultiplicator=1] [, sigma=0] [, useAlpha=0] [, method=0])  
  
Creates a procedural texture that allows to draw sine grating stimulus patches  
with a smoothed aperture in a very fast and efficient manner on modern   
graphics hardware.  
  
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
  
'sigma' Optional. Edge smoothing value in pixels. Defaults to 0.  
  
'useAlpha' Optional, defaults to 0. Whether to use color (0) or alpha (1)  
 for smoothing channel. Defaults to 0 (color).  
  
'method' Optional. Whether to use cosine (0), smoothstep(1) or   
 inverse smoothstep (2) smoothing function. Defaults to 0 (cosine).  
  
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
  
### For a zero degrees grating without aperture (radius = inf):  
  
g(x,y) = modulatecolor \* contrast \* contrastPreMultiplicator \* sin(x\*2\*pi\*freq + phase) + Offset  
  
NOTE: The modulation is also applied to the alpha channel, so if you use alpha  
blending, make sure to take this into account, e.g., by setting the alpha component  
of modulateColor - or the globalAlpha parameter - to zero, if you don't want the  
alpha channel modulated by a sine wave as well! Then you can use the alpha component  
of backgroundColorOffset to write a constant alpha value. Or you can use the  
[Screen](Screen)('Blendfunction', ...) to set the color write mask to prevent alpha channel  
updates.  
  
For a zero degrees grating with aperture (radius = some non-infinite value) iff  
'useAlpha' is set to zero or false:  
  
g(x,y) = modulatecolor \* contrast \* contrastPreMultiplicator \* sin(x\*2\*pi\*freq + phase) \* weight(dist(x,y), radius, sigma) + Offset  
  
weight(dist(x,y), radius, sigma) is a weighting function which is 1.0 for a dist(x,y)  
position on a circle around the center within 'radius' - 'sigma', then  
falls off to 0.0 for positions inside a circle between 'radius' - 'sigma' and  
'radius', in other words, the sine grating "fades out" to zero contrast at the  
border inside 'radius' over a range of 'sigma' pixels. The specific weight()ing  
function can be selected via the 'method' parameter: It is either a cosine falloff,  
or a linear falloff.  
  
Again, alpha channel is also affected the same way.  
  
For a zero degrees grating with aperture (radius = some non-infinite value) iff  
'useAlpha' is set to 1 or true:  
  
g(x,y).rgb = modulatecolor.rgb \* contrast \* contrastPreMultiplicator \* sin(x\*2\*pi\*freq + phase) + Offset.rgb  
  
As you can see, the color channels rgb are calculated without an aperture applied,  
and the aperture weight function is instead applied to the alpha channel only:  
  
g(x,y).a = modulateColor.a \* weight(dist(x,y), radius, sigma) + Offset.a  
  
This makes only sense if you enable alpha blending to apply the falloff!  
  
  
Make sure to use the [Screen](Screen)('DrawTextures', ...); function properly to  
draw many different gratings simultaneously - this is much faster!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedApertureSineGrating.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedApertureSineGrating.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralSmoothedApertureSineGrating.m</code>
</div>

