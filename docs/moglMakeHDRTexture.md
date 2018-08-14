# [moglMakeHDRTexture](moglMakeHDRTexture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

textureId = moglMakeHDRTexture(win, hdrImage [, halffloat][, poweroftwo])  
  
Create a high dynamic range Psychtoolbox texture from the given  
Matlab/Octave high dynamic range image matrix 'hdrImage' and attach  
it to the onscreen window 'win'.  
  
Before calling this function you must have called [Screen](Screen)('BeginOpenGL', win);  
with 'win' being the window handle for the onscreen window to  
which the texture should be attached.  
  
Returns a Psychtoolbox handle 'textureId' for the created 2D texture.  
The texture can be used like any other Psychtoolbox texture, just  
with the difference that it represents its color values with 32 bit  
floating point precision or 16 bit half floating point precision  
instead of 8 bpc fixed point precision.  
  
The optional flag 'halffloat', if set to 1, will trigger creation of a  
texture in half float format, ie. 16 bit floating point numbers instead  
of 32 bit ones. This saves 50% memory and bandwidth. It also allows to  
apply bilinear filtering during texture blits in hardware on [GeForce](GeForce) 6000  
and higher.  
  
Normally, Psychtoolbox will try to select a GL\_TEXTURE\_RECTANGLE  
texture if the hardware supports it. You can enforce creation of  
a power-of-two GL\_TEXTURE\_2D by setting the optional 'poweroftwo'  
flag to a value of 1.  
  
'hdrImage' must be a (height, width, 4) matrix of type 'double' or  
'single', where channel 1=Red, 2=Green, 3=Blue, 4=Alpha. The numeric  
range (0.0 - 1.0) maps to (minimum intensity - maximum intensity).  
  
If you want to use the created 2D texture for 3D [OpenGL](OpenGL) rendering  
as well, you can use the [Screen](Screen)('GetOpenGLTexture') function to  
retrieve a standard [OpenGL](OpenGL) texture handle to it.  
  
If you don't want to create a pure 2D texture, but a cube map texture  
for use in 3D environment mapped lighting and such, then use the  
function moglMakeGLHDRTexture() instead. It can create cube-map  
textures for use with the [OpenGL](OpenGL) functions. These are not useable  
with the standard Psychtoolbox [Screen](Screen)() commands.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglMakeHDRTexture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglMakeHDRTexture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglMakeHDRTexture.m</code>
</div>

