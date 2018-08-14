# [kPsychNeedFinalizedFBOSinks](kPsychNeedFinalizedFBOSinks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedFinalizedFBOSinks  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to tell [Screen](Screen)'s imaging pipeline that  
the final output image - after all post-processing - should not be  
written to the onscreen windows [OpenGL](OpenGL) system backbuffer for presentation  
in the onscreen window/on the onscreen windows associated display  
device. Instead it should be written to an [OpenGL](OpenGL) framebuffer object,  
more specifically to a non-power of two GL\_TEXTURE\_2D [OpenGL](OpenGL) texture  
attached to that [OpenGL](OpenGL) framebuffer object. The resulting [OpenGL](OpenGL) texture  
can then be used as a source image for further processing or display by  
non-standard display sinks, e.g., by the VR compositor of a Virtual Reality  
head mounted display, or some highly specialized non-standard proprietary  
display hardware.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedFinalizedFBOSinks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedFinalizedFBOSinks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedFinalizedFBOSinks.m</code>
</div>

