# [DriftDemo4](DriftDemo4)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

function [DriftDemo4](DriftDemo4)([angle=0][, cyclespersecond=1][, freq=1/360][, gratingsize=360][, internalRotation=0])  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Display an animated grating, using the new [Screen](Screen)('DrawTexture') command.  
This demo demonstrates fast drawing of such a grating via use of procedural  
texture mapping. It only works on hardware with support for the GLSL  
shading language, vertex- and fragmentshaders. The demo ends if you press  
any key on the keyboard.  
  
The grating is not encoded into a texture, but instead a little algorithm - a  
procedural texture shader - is executed on the graphics processor (GPU)  
to compute the grating on-the-fly during drawing.  
  
This is very fast and efficient! All parameters of the grating can be  
changed dynamically. For a similar approach wrt. Gabors, check out  
[ProceduralGaborDemo](ProceduralGaborDemo). For an extremely fast aproach for drawing many Gabor  
patches at once, check out [ProceduralGarboriumDemo](ProceduralGarboriumDemo). That demo could be  
easily customized to draw many sine gratings by mixing code from that  
demo with setup code from this demo.  
  
Optional Parameters:  
'angle' = Rotation angle of grating in degrees.  
'internalRotation' = Shall the rectangular image patch be rotated  
(default), or the grating within the rectangular patch?  
gratingsize = Size of 2D grating patch in pixels.  
freq = Frequency of sine grating in cycles per pixel.  
cyclespersecond = Drift speed in cycles per second.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DriftDemo4.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DriftDemo4.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DriftDemo4.m</code>
</div>

