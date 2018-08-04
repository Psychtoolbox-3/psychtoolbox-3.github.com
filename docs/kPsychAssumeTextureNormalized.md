# [kPsychAssumeTextureNormalized](kPsychAssumeTextureNormalized)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGLImageProcessing](PsychGLImageProcessing)

rc = kPsychAssumeTextureNormalized  
  
Returns a flag to be passed to the 'specialFlags' optional argument of  
[Screen](Screen)('TransformTexture');  
  
The flag tells the command that the input texture(s) are already in a  
normalized upright format, regardless what the textures themselves claim.  
This allows to save on some internal format conversion overhead if the  
textures are really normalized, or if you can use some hacks in your code  
to at least fake that situation.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGLImageProcessing/kPsychAssumeTextureNormalized.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGLImageProcessing/kPsychAssumeTextureNormalized.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGLImageProcessing/kPsychAssumeTextureNormalized.m</code>
</div>

