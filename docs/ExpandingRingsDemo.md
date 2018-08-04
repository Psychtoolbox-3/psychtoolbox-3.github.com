# [ExpandingRingsDemo](ExpandingRingsDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[ExpandingRingsDemo](ExpandingRingsDemo)([ringtype=0]) -- Generate an "expanding rings"  
stimulus by use of GLSL shaders and Psychtoolbox procedural textures.  
  
This demo illustrates the use of "procedural textures" with Psychtoolbox.  
A procedural texture is a texture that is not directly represented by an  
image matrix in memory, but the image content of the texture is generated  
on the fly during drawing of the texture by means of a small algorithm -  
a shader. The shader implements some mathematical formula or model which  
is evaluated to generate image content, or it reads content of a data  
matrix and transforms it into a picture. Psychtoolbox supports both,  
purely virtual textures of unlimited size that are purely algorithmically  
generated, and hybrid textures where an algorithm transforms the textures  
content into something to be drawn.  
  
The algorithm has to be implemented by a GLSL shader program - a vertex  
shader, geometry shader, fragment shader or any combination of them. The  
shader program is read from a file, compiled and then attached to the  
texture at texture creation time. Procedural textures only work with  
graphics hardware that has sufficiently advanced support for (at least)  
hardware fragment shaders.  
  
This demo implements a procedural texture which shows a set of rings that  
can expand and move. The shader gets attached to a purely virtual  
texture. The texture is drawn via the standard [Screen](Screen)('DrawTexture')  
command -- your graphics processor generates the image content of the  
stimulus on the fly during drawing of the texture via execution of the  
shader at each output pixel location.  
  
The optional 'ringtype' parameter allows to select between different ring  
shapes. Default type is zero:  
  
0 = Hard transitions between red and yellow rings.  
1 = Transitions are modeled as a smooth sine wave, softly fading from  
    yellow to red and back.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/ExpandingRingsDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/ExpandingRingsDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/ExpandingRingsDemo.m</code>
</div>

