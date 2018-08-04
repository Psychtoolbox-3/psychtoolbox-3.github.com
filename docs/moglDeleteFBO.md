# [moglDeleteFBO](moglDeleteFBO)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

moglDeleteFBO(fbo) -- Delete FBO 'fbo' and its associated buffers and textures.  
  
This function is mostly useful for image processing and GPGPU  
applications. Normal Psychtoolbox code will want to use standard  
Offscreen windows instead. They are properly managed by Psychtoolbox for  
normal stimulus drawing and implemented to work on any kind of hardware,  
whereas this function is optimized for [OpenGL](OpenGL)-2 compliant hardware.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglDeleteFBO.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglDeleteFBO.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglDeleteFBO.m</code>
</div>

