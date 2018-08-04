# [ScreenDacBits](ScreenDacBits)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

dacBits = [ScreenDacBits](ScreenDacBits)(windowPtrOrScreenNumber)  
  
What is the precision of the [DACs](DACs) on this graphics card?  
  
At present you need to know the bit depth of your graphics board's DAC  
to determine how to write its CLUT, i.e. [Screen](Screen) 'SetClut' or 'Gamma'.  
Use this routine and [ScreenUsesHighGammaBits](ScreenUsesHighGammaBits), instead of the the brand-  
and platform-specific [IsRadiusThunder10](IsRadiusThunder10) and [IsATIRadeon10](IsATIRadeon10), to keep your  
program as general as possible, not tied to particular hardware or  
platform.  
  
The value is set in [PrepareScreen](PrepareScreen).m.  
  
See also [LoadClut](LoadClut), [ScreenPixelSize](ScreenPixelSize), [ScreenUsesHighGammaBits](ScreenUsesHighGammaBits), [ScreenClutSize](ScreenClutSize).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/ScreenDacBits.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/ScreenDacBits.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/ScreenDacBits.m</code>
</div>

