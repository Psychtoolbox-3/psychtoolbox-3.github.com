# [MacBoynToLMS](MacBoynToLMS)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[LMS, factorsLMS] = [MacBoynToLMS](MacBoynToLMS)(lsY,T\_cones,T\_lum)  
  
Convert Macleod-Boynton chromaticity together with luminance to  
cone coordinates.  
  
This is designed to be used with the modern form of [LMSTOMacBoyn](LMSTOMacBoyn),  
namely  
  lsY = [LMSToMacBoyn](LMSToMacBoyn)(LMS2,T\_cones,T\_Y,1);  
as this form returns both ls and the corresponding luminance.  Passing  
both cone fundamentals and luminance sensitivity (T\_cones and T\_Y) keeps  
the routine general.  The scaling of s is also consistent when the calls  
are done in this way.  
  
See usage example in [LMSToMacBoyn](LMSToMacBoyn).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/MacBoynToLMS.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/MacBoynToLMS.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/MacBoynToLMS.m</code>
</div>

