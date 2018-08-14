# [moglBlitTexture](moglBlitTexture)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

moglBlitTexture(texid, x, y, w, h, fastblit, clamping)  
  
moglBlitTexture blits the [OpenGL](OpenGL) texture 'texid' at offset (x,y) into the  
current framebuffer. 'w x h' pixels are blitted. By default the offset is  
(0,0), the size is the full size of the texture.  
  
If you set the fastblit - flat to 1, then all other parameters are  
required, all error-checking and texture engine setup is skipped and only  
the minimal amount of code for initiating a blit is performed. This is  
useful in inner loops of GPGPU algorithms to squeeze out more speed!  
  
This does basically the same as [Screen](Screen)('DrawTexture') but without all the  
convenience stuff contained in 'DrawTexture' - and without the possible  
interference of PTB's internal drawing model. This is mostly useful for  
GPGPU and image processing applications where one needs very strict  
control of the way drawing is done. For everything else, use  
[Screen](Screen)('DrawTexture').  
  
Current limitation: Only rectangle textures are supported.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglBlitTexture.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglBlitTexture.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglBlitTexture.m</code>
</div>

