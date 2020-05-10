# [CreateProceduralColorGrating](CreateProceduralColorGrating)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

[id, rect, shader] = [CreateProceduralColorGrating](CreateProceduralColorGrating)(windowPtr, width,  
height [, color1=[1 0 0]]  [, color2=[0 1 0]] [, radius=0])  
  
A procedural color grating shader that can generate either sinusoidal or  
square gratings varying between two colors.   
  
  
### INPUT VALUES:  
  
\* width, height = "virtual size" of the GLSL shader.  
\* color1, color2 = two colors for the grating peaks to vary between. When  
  running (see [ProceduralColorGratingDemo)](ProceduralColorGratingDemo)), you can pass baseColor parameter,  
  from which color1 and color2 will be modulated via the contrast parameter.  
  When contrast is 0, then color1 and color2 are the same as baseColor. As  
  contrast increases each color is mixed with baseColor until at contrast 1   
  the grating peaks are color1 and color2 exactly. Color mixing uses  
  OpenGL's mix command.   
\* radius = optional hard-edged circular mask sized in pixels.  
  
  
### RETURN VALUES:   
  
\* id = texture pointer.  
\* rect = rect describing the size and shape of the texture.  
\* shader = the GLSL shader, useful if you want to use glUniform commands to  
  modify color 1, color2 or radius after texture creation.  
  
  
### DRAWING MODIFIERS:  
  
When drawing this shader using [Screen](Screen)('DrawTexture|s'), you can pass  
additional values:  
  
\* baseColor is the base color from which color1 and color2 are mixed.  
\* contrast is the mixing amount from baseColor to color1 and color2.  
\* sigma is a smoothing value, when sigma == -1 a sinusoidal grating is  
  produced; and when sigma \>= 0 a square wave grating is produced using sigma  
  value of smoothing at the edge.   
  
  
### TEXTURE DETAILS:  
  
Color blending (blending each color to the baseColor, and then blending  
with each other) uses GLSL mix function; mix performs a linear  
interpolation between x and y using a to weight between them. The return  
value is computed as: $x \times (1 - a) + y \times a$. See  
<http://docs.gl/sl4/mix\> for more details.  
  
Smoothing uses GLSL smoothstep function that uses hermite interpolation.  
A small amount of smoothing for squarewave grating edges can reduce  
jumping artifacts when squarewave gratings are drifted. See  
<http://docs.gl/sl4/smoothstep\> for more details.  
  
  
See also: [CreateProceduralSineGrating](CreateProceduralSineGrating), [CreateProceduralSineSquareGrating](CreateProceduralSineSquareGrating)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralColorGrating.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateProceduralColorGrating.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateProceduralColorGrating.m</code>
</div>

