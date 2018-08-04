# [moglChooseFBO](moglChooseFBO)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

moglChooseFBO(fbo, bufferid) -- Set FBO 'fbo' as framebuffer.  
  
If fbo is \> 0, then the corresponding FBO is bound and [OpenGL](OpenGL) is set up  
to render and read from that FBO with orthogonal projection. If fbo is  
zero, then the system framebuffer is enabled again for normal drawing.  
  
Normally, read- and writebuffer are set to color attachment zero. If you  
provide bufferid, then it is set to bufferid, with 1 being the first  
attachment (COLOR\_ATTACHMENT0\_EXT).  
  
This function is mostly useful for image processing and GPGPU  
applications. Normal Psychtoolbox code will want to use standard  
Offscreen windows instead. They are properly managed by Psychtoolbox for  
normal stimulus drawing and implemented to work on any kind of hardware,  
whereas this function is optimized for [OpenGL](OpenGL)-2 compliant hardware.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglChooseFBO.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglChooseFBO.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglChooseFBO.m</code>
</div>

