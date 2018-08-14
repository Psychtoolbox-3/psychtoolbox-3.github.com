# [kPsychSinkIsMSAACapable](kPsychSinkIsMSAACapable)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychSinkIsMSAACapable  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') together with the 'kPsychNeedFinalizedFBOSinks'  
flag. If this kPsychSinkIsMSAACapable flag is given then the  
[OpenGL](OpenGL) framebuffer objects which are created and attached as final  
output image sinks due to the 'kPsychNeedFinalizedFBOSinks' flag will  
be allowed to have GL\_TEXTURE\_2D\_MULTISAMPLE textures as color attachments,  
and thereby as final target of the output images. Iow., the sink can  
handle multisampled textures.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSinkIsMSAACapable.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychSinkIsMSAACapable.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychSinkIsMSAACapable.m</code>
</div>

