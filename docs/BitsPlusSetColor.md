# [BitsPlusSetColor](BitsPlusSetColor)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)

[SetColorBitspp](SetColorBitspp)(windowPtr,entry,rgb)  
  
Set the specified entry of the clut, using the Bits++ box and our  
frame buffer conventions.  
  
Prior to using this routine, Bits++ box must be in  
framebuffer load mode.  
  
This routine is not required to be speedy, and it isn't.  
  
xx/xx/02  jmh  Wrote it, but didn't comment.  
2/23/03   dhb  Added comments.  
2/28/03   dhb, ptw  Add delay to make sure glitch has settled.  
               Changed name, fixed up.  
3/8/03    dhb  Remove call to bitsplus.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusSetColor.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusSetColor.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusSetColor.m</code>
</div>

