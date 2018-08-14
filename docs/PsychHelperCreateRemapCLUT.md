# [PsychHelperCreateRemapCLUT](PsychHelperCreateRemapCLUT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

remapCLUTId = [PsychHelperCreateRemapCLUT](PsychHelperCreateRemapCLUT)(cmd, arg);  
  
Helper function for Psychtoolbox imaging pipeline, called by  
[PsychImaging](PsychImaging)(), not meant to be called by normal user code!  
  
### If 'cmd' command code is zero, then:  
  
Build a 3 rows by arg1 texels RGBA8 lookup texture for mapping of RGB  
pixel values in range 0 to (arg-1) to RGBA8 framebuffer pixels. This  
texture is used as CLUT texture for the  
[RGBMultiLUTLookupCombine](RGBMultiLUTLookupCombine)\_FormattingShader.frag.txt in the image  
processing chains of the imaging pipeline. If arg2 is set to 1 instead of  
zero, a 32 bpc float texture is used instead of 8 bpc integer.  
  
If 'cmd' command code is 1, then the clut texture with id arg1 is updated  
with the content of clut table arg2.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateRemapCLUT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateRemapCLUT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/PsychHelperCreateRemapCLUT.m</code>
</div>

