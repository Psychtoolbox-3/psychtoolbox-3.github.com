# [kPsychNeedOtherStreamInput](kPsychNeedOtherStreamInput)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rval = kPsychNeedOtherStreamInput  
  
Return a flag that you can pass to the 'imagingmode' parameter of  
[Screen](Screen)('OpenWindow') in order to allow shaders in stereo configurations  
to access both eyes input images.  
  
Normally only the stereo compositing chain of the pipeline can access  
both image buffers for left-eye and right-eye view. This flag also enables  
access during the per-view image processing chain, and during the per  
view output formatting/post-processing chain. Logic for these chains is  
that the primary image channel is bound to texture unit 0 as usual, but  
additionally now the other channel (right channel for left view processing,  
and left channel for right view processing) is bound to texture unit 1.  
  
Caution: The secondary channel is bound with nearest neighbour filtering.  
Caution: The shaders in one of these chains will only have access to the  
secondary channels initial input image for their chains (inputimageFBO in case  
of the image processing chain, preConversionFBO in case of output conversion  
/ final formatting). Multi-Pass chains have to take this into account that the  
secondary channel won't update during multi-stage processing, but stays static.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedOtherStreamInput.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychNeedOtherStreamInput.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychNeedOtherStreamInput.m</code>
</div>

