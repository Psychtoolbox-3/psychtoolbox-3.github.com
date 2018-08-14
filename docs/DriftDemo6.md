# [DriftDemo6](DriftDemo6)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

function [DriftDemo6](DriftDemo6)(angle, cyclespersecond, f)  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
This demo demonstrates how to use [Screen](Screen)('DrawTexture') in combination  
with GLSL texture draw shaders to efficiently combine two drifting  
gratings with each other.  
  
The demo shows a drifting sine grating through a circular aperture. The  
drifting grating is surrounded by an annulus (a ring) that shows a second  
drifting grating with a different orientation.  
  
The demo ends after a key press or after 60 seconds have elapsed.  
  
The demo needs modern graphics hardware with shading support, otherwise  
it will abort.  
  
Compared to previous demos, we apply the aperture to the grating texture  
while drawing the grating texture, ie. in a single drawing pass, instead  
of applying it in a 2nd pass after the grating has been drawn already.  
This is simpler and faster than the dual-pass method. For this, we store  
the grating pattern in the luminance channel of a single texture, and the  
alpha-mask in the alpha channel of \*the same texture\*. During drawing, we  
apply a special texture filter shader (created via  
[MakeTextureDrawShader](MakeTextureDrawShader)()). This shader allows to treat the alpha channel  
separate from the luminance or rgb channels of a texture: It applies the  
alpha channel "as is", but applies some shift to the luminance or rgb  
channels of the texture.  
  
The procedure is repeated with a 2nd masked texture to create two  
different drifting gratings, superimposed to each other.  
  
Please note that the same effect can be achieved by clever alpha blending  
on older hardware, e.g., see [DriftDemo5](DriftDemo5). The point of this demo is to  
demonstrate how to use GLSL shaders for more efficient ways of  
manipulating textures during drawing.  
  
### Parameters:  
  
angle = Angle of the gratings with respect to the vertical direction.  
cyclespersecond = Speed of gratings in cycles per second.  
f = Frequency of gratings in cycles per pixel.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also: [PsychDemos](PsychDemos), [MovieDemo](MovieDemo)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DriftDemo6.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DriftDemo6.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DriftDemo6.m</code>
</div>

