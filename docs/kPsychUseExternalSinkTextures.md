# [kPsychUseExternalSinkTextures](kPsychUseExternalSinkTextures)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychUseExternalSinkTextures  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') together with the 'kPsychNeedFinalizedFBOSinks'  
flag. If this kPsychUseExternalSinkTextures flag is given then the  
[OpenGL](OpenGL) framebuffer objects which are created and attached as final  
output image sinks due to the 'kPsychNeedFinalizedFBOSinks' flag will  
not use [Screen](Screen)() internally created [OpenGL](OpenGL) textures as color attachments,  
and thereby as final target of the output images. Instead, externally  
created suitable (color render-to-texture capable) non-power-of-two  
[OpenGL](OpenGL) textures will get dynamically attached as render targets during  
the relevant render pass. Producers of such external target textures can  
be 3rd party [SDKs](SDKs) or runtimes, e.g., the Oculus VR 1.x SDK and runtime  
which would send such textures with the final rendered output images to  
a VR compositor for output on a suitable VR headset. Other applications  
are conceivable, but this is the initial target application of this flag.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychUseExternalSinkTextures.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychUseExternalSinkTextures.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychUseExternalSinkTextures.m</code>
</div>

