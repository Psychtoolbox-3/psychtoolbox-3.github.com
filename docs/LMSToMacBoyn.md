# [LMSToMacBoyn](LMSToMacBoyn)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

ls = [LMSToMacBoyn](LMSToMacBoyn)(LMS,[T\_cones,T\_lum])  
  
Compute [MacLeod](MacLeod)-Boynton chromaticity from  
cone coordinates.  
  
If T\_cones and T\_lum are not passed, we assume  
Smith-Pokorny sensitivities normalized to a  
peak of 1.  I T\_cones and T\_lum are passed,  
we compute the scalings of the L and M cones  
required to best predict lumiance and scale  
accordingly.  
  
10/30/97  dhb  Wrote it.  
7/9/02    dhb  T\_cones\_sp -\> T\_cones on line 20.  Thanks to Eiji Kimura.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/LMSToMacBoyn.m</code>
</div>

