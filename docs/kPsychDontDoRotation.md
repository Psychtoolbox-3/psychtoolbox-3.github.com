# [kPsychDontDoRotation](kPsychDontDoRotation)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

kPsychDontDoRotation  
  
Returns a constant to be passed as part of the 'specialFlags' parameter  
of the [Screen](Screen)('DrawTexture') and [Screen](Screen)('DrawTextures') command.  
  
If this flag is set, the texture drawing functions will not apply texture  
Rotation by themselves, even if the 'rotationAngle' parameter is  
non-zero. Instead they will just pass the 'rotationAngle' parameter to a  
GLSL shader if any is enabled, so the shader can implement its own way of  
"rotating" the texture to be drawn. This allows for custom  
implementations of texture drawing.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/kPsychDontDoRotation.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/kPsychDontDoRotation.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/kPsychDontDoRotation.m</code>
</div>

