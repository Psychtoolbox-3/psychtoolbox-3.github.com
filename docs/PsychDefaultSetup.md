# [PsychDefaultSetup](PsychDefaultSetup)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

[PsychDefaultSetup](PsychDefaultSetup)(featureLevel) - Perform standard setup for Psychtoolbox.  
  
This function performs a few typical "boilerplate" setup operations  
at the beginning of a script to avoid repetitive code at the top of  
a script.  
  
Add it at the top of your script, so all its settings affect successive  
Psychtoolbox commands.  
  
The parameter 'featureLevel' determines what kind of setup is  
specifically performed. A higher number for 'featureLevel' will  
include all setup steps and default settings for lower numbers  
of 'featureLevel' and extend on them. E.g., a featureLevel of 2 would  
imply all setup operations of featureLevel 0 and 1, plus some new  
additional setup operations.  
  
A 'featureLevel' of 0 will do nothing but execute the [AssertOpenGL](AssertOpenGL) command,  
to make sure that the [Screen](Screen)() mex file is properly installed and functional.  
  
A 'featureLevel' of 1 will additionally execute [KbName](KbName)('UnifyKeyNames') to  
provide a consistent mapping of keyCodes to key names on all operating  
systems.  
  
A 'featureLevel' of 2 will additionally imply the execution of  
[Screen](Screen)('ColorRange', window, 1, [], 1); immediately after and whenever  
[PsychImaging](PsychImaging)('OpenWindow',...) is called, thereby switching the default  
color range from the classic 0-255 integer number range to the normalized  
floating point number range 0.0 - 1.0 to unify color specifications  
across differently capable display output devices, e.g., standard 8 bit  
displays vs. high precision 16 bit displays. Please note that clamping of  
valid color values to the 0 - 1 range is still active and colors will  
still be represented by 256 discrete levels (8 Bit resolution), unless  
you also use [PsychImaging](PsychImaging)() commands to request unclamped color  
processing or floating point precision framebuffers. This function by  
itself only changes the range, not the precision of color specifications!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/PsychDefaultSetup.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/PsychDefaultSetup.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/PsychDefaultSetup.m</code>
</div>

