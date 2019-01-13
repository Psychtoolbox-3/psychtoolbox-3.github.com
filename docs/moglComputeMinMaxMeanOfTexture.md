# [moglComputeMinMaxMeanOfTexture](moglComputeMinMaxMeanOfTexture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)>[PsychGLSLShaders](PsychGLSLShaders)

[minv, maxv, meanv] = moglComputeMinMaxMeanOfTexture(texid, pingpongfbo1, pingpongfbo2, fastpath)  
  
This function expects a square RGB texture as input, whose color channels  
contain identical values L=R=G=B where L is a grayscale (luminance) input  
image. It computes and returns its global minimum, maximum and mean luminance  
on the GPU.  
  
The width and height of the texture need to be divisible by two (even numbers).  
It only works on RECTANGLE textures, not on standard power-of-two textures!  
You are not allowed to use an input texture 'texid' that is identical to  
the color buffer texture of the FBO 'pingpongfbo2'!  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/moglComputeMinMaxMeanOfTexture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/PsychGLSLShaders/moglComputeMinMaxMeanOfTexture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/PsychGLSLShaders/moglComputeMinMaxMeanOfTexture.m</code>
</div>

