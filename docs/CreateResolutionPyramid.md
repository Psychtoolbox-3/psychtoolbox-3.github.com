# [CreateResolutionPyramid](CreateResolutionPyramid)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

Build a mip-map image resolution pyramid for given texture.  
  
[CreateResolutionPyramid](CreateResolutionPyramid)(tex [, glsl=0][, usebilinear=0])  
  
'tex' must be the [Screen](Screen)() texture or offscreen window handle of a  
texture or offscreen window of type GL\_TEXTURE\_2D, ie., created with  
'specialFlags' setting 1. The function will create a [OpenGL](OpenGL) mip-map  
resolution pyramid by successive downsampling of 'tex' image content down  
to a image of 1x1 pixels. If 'glsl' is provided as handle to a shader, it  
will use that shader to do the downsampling, otherwise it will use  
bilinear filtering for successive pyramid levels. If 'usebilinear' is set  
to 1 it will feed the shader with linear interpolated samples, otherwise  
with nearest neighbour samples.  
  
You will likely also want to set 'specialFlags' flag 8 or 16 to prevent  
[Screen](Screen)('DrawTexture') from overwriting the image pyramid with its own  
auto-generated one.  
  
This needs a modern GLSL shading capable graphics card to work.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/CreateResolutionPyramid.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/CreateResolutionPyramid.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/CreateResolutionPyramid.m</code>
</div>

