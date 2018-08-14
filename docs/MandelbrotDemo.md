# [MandelbrotDemo](MandelbrotDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[MandelbrotDemo](MandelbrotDemo) -- GPU visualization of the fractal Mandelbrot set.  
  
This demo illustrates the use of "procedural textures" with Psychtoolbox.  
A procedural texture is a texture that is not directly represented by an image  
matrix in memory, but the image content of the texture is generated on  
the fly during drawing of the texture by means of a small algorithm - a  
shader. The shader implements some mathematical formula or model which is  
evaluated to generate image content, or it reads content of a data  
matrix and transforms it into a picture. Psychtoolbox supports both,  
purely virtual textures of unlimited size that are purely algorithmically  
generated, and hybrid textures where an algorithm transforms the textures  
content into something to be drawn.  
  
The algorithm has to be implemented by a GLSL shader program - a vertex shader,  
primitive shader, fragment shader or any combination of them. The shader  
program is read from a file, compiled and then attached to the texture on  
texture creation time. Procedural textures only work with graphics  
hardware that has sufficiently advanced support for at least hardware  
fragment shaders.  
  
This demo implements the mathematical formula for visualization of the  
famous fractal Mandelbrot set in a fragment shader. The shader gets  
attached to a purely virtual texture. The texture is drawn via the  
standard [Screen](Screen)('DrawTexture') command -- your graphics processor  
generates the image content of the Mandelbrot set on the fly during  
drawing of the texture via evaluation of the mandelbrot formula.  
Selecting a subregion (the sourceRect parameter of 'DrawTexture') allows  
to zoom into a specific subregion of the Mandelbrot set.  
  
The implementation uses up to 150 iterations of the equation for each  
drawn pixel, so it may be slow on old hardware.  
  
In the demo, use gentle mouse movements to scroll around in the set and  
the left- right- mouse button to zoom into/out of the set. Press any key  
on the keyboard to exit the demo.  
  
Wikipedia http://www.wikipedia.org has a nice explanation of the  
Mandelbrot set under the search term "Mandelbrot set".  
  
The shader used for this demo is part of the "Orange book" - The guide to  
the [OpenGL](OpenGL) Shading language. The code is copyright 3DLabs. See the  
3DLabs-License.txt file in the [PsychDemos](PsychDemos)/[OpenGLDemos](OpenGLDemos)/[GLSLDemoShaders](GLSLDemoShaders)/  
subfolder for the license.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/MandelbrotDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/MandelbrotDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/MandelbrotDemo.m</code>
</div>

