# [BitsPlusImagingMonoTest](BitsPlusImagingMonoTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusTests](BitsPlusTests)

[BitsPlusImagingMonoTest](BitsPlusImagingMonoTest)([testdrawingcmds])  
  
Test of built-in Mono++ output conversion shader of PTB  
imaging pipeline. This is meant to test Bits++ Mono++  
conversion of GPU against reference implementation of  
Matlab [BitsPlus](BitsPlus) toolbox.  
  
First the stimulus is generated via Matlab conversion routine.  
Then it is drawn via PTB imaging pipeline conversion.  
Then the PTB imaging result is read back and compared against  
the result of the Matlab implementation and the maximum error  
is returned. This error should be zero.  
  
The optional parameter 'testdrawingcmds' specs if pure texture  
mapping should be tested, or if a combo of texture mapping and  
[Screen](Screen) 2D drawing commands gets tested (1).  
  
THIS TEST IS NOT FINISHED. EARLY BETA.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingMonoTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingMonoTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingMonoTest.m</code>
</div>

