# [bitsGoggles](bitsGoggles)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)

[encodedDIOdata] = bitsGoggles(left, right [, window])  
  
Drives the FE1 goggles connected to bits 4 and 5 of the digital output  
of a Bits+, Bits\#, etc.  
  
'left' and 'right' define the required state of the left and  
right goggle shutter, where a value of:  
0 = goggle open  
1 = goggle closed  
  
If 'window' is given, but the return argument 'encodedDIOdata' is not  
given, then the control code is drawn into the framebuffer and a flip  
is performed.  
  
If 'encodedDIOdata' is given, then 'window' is not used  
and the required T-Lock code is returned as a image matrix  
which could be used for [Screen](Screen)('PutImage') or [Screen](Screen)('DrawTexture').  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/bitsGoggles.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/bitsGoggles.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/bitsGoggles.m</code>
</div>

