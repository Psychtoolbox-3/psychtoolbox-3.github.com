# [BitsPlusImagingColorImageTest](BitsPlusImagingColorImageTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[BitsPlusToolbox](BitsPlusToolbox)>[BitsPlusTests](BitsPlusTests)

[BitsPlusImagingColorImageTest](BitsPlusImagingColorImageTest)([realimage][, imagefile][, plotdiffs])  
  
Test use of Color++ mode with imaging pipeline...  
  
Renders a HDR color image, converts it to Bits++ Color++ format, once via  
Matlab Bits++ toolbox function [BitsPlusPackColorImage](BitsPlusPackColorImage) and once via GPU  
based imaging pipeline. Reads back and compares results to assess  
correctness and accuracy of the new GPU implementation.  
  
realimage = 0 (Default) Create color gradient pattern with all 65535  
possible values for a systematic test.  
  
realimage = 1 Load an example HDR image of a "real" rendered scene for  
comparison.  
  
### UNFINISHED BETA CODE!  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingColorImageTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingColorImageTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/BitsPlusToolbox/BitsPlusTests/BitsPlusImagingColorImageTest.m</code>
</div>

