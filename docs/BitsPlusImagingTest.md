# [BitsPlusImagingTest](BitsPlusImagingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusTests](BitsPlusTests)

[BitsPlusImagingTest](BitsPlusImagingTest)([whichScreen])  
  
Simple test of Bits++ interface in normal mode.  Writes CLUT  
frame buffer, so this is how Bits++ should be configured to  
accept it.  
  
This test routine employs the PTB imaging pipeline to do the  
job.  
  
If the optional 'whichScreen' screen index of the Bits++ screen is left  
out, the script will choose the display with the highest screen id.  
  
### If everything works correctly, you should see the following:  
  
1. First some random color "junk" on the Bits++ display for 3 seconds.  
2. Then a black screen.  
3. Then, on each keystroke, an increase in display luminance.  
4. After twenty keystrokes, a fully white display.  
5. After another keystroke, the Bits++ should revert to a normal desktop  
   display.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingTest.m</code>
</div>

