# [moglMakeGLHDRTexture](moglMakeGLHDRTexture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

gltexId = moglMakeGLHDRTexture(hdrImage, gltextarget [, halffloat])  
  
Create a high dynamic range [OpenGL](OpenGL) texture from the given  
Matlab/Octave high dynamic range image matrix 'hdrImage' and attach  
it to the [OpenGL](OpenGL) texture target of type 'gltextarget'.  
  
Before calling this function you must have called [Screen](Screen)('BeginOpenGL', win);  
with 'win' being the window handle for the onscreen window to  
which the texture should be attached.  
  
Returns an [OpenGL](OpenGL) texture handle 'gltexId' for the created texture.  
The texture can be used like any other [OpenGL](OpenGL) texture, just  
with the difference that it represents its color values with 32 bit  
floating point precision instead of 8 bpc fixed point precision.  
  
'hdrImage' must be a (height, width, 4) matrix of type 'double' or  
'single', where channel 1=Red, 2=Green, 3=Blue, 4=Alpha. The numeric  
range (0.0 - 1.0) maps to (minimum intensity - maximum intensity).  
  
If 'halffloat' is set to 1 (default is 0), then the texture is created as  
half-precision floating point texture, ie 16 bpc floats. This saves  
memory and bandwidth and allows for floating point filtering on Geforce  
6000 and 7000 series.  
  
If you want to create a pure 2D texture and use it with Psychtoolbox'  
standard [Screen](Screen)() drawing command, then call moglMakeHDRTexture() instead.  
  
This function is most useful if you want to create textures not handled  
by Psychtoolbox, i.e., cube map textures for environment mapping and  
texture based lighting.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglMakeGLHDRTexture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglMakeGLHDRTexture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglMakeGLHDRTexture.m</code>
</div>

