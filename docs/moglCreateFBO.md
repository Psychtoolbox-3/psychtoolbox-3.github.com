# [moglCreateFBO](moglCreateFBO)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

[fbo , texids] = moglCreateFBO(width, height [, nrbuffers, layers, format, withdepth, withstencil])  
  
moglCreateFBO creates a standard [OpenGL](OpenGL) Framebuffer Object, suitable for  
computer vision and other GPGPU tasks and returns a handle to it.  
  
The FBO will have a size of width x height pixels and its 'nrbuffers'  
color buffers will have textures with 'layers' layers (default = 4 for RGBA)  
attached.  
'format' specifies the data format. It defaults to single precision  
floating point resolution (32 bit float). If 'withdepth' \> 0 then a  
depth buffer gets attached as well. If 'withstencil' \> 0 then a stencil  
drawable gets attached as well.  
  
The function will create appropriate textures and renderbuffers, create  
an appropriate FBO and attach the textures and renderbuffers. After  
validation, the handle to the FBO is returned.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglCreateFBO.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglCreateFBO.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglCreateFBO.m</code>
</div>

