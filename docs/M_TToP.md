# [M_TToP](M_TToP)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[M] = M\_TToP(Tsource,Pdest)  
[M,dest] = M\_TToP(Tsource,Pdest,source)  
  
Compute the conversion matrix between a color  
space with known primaries and one with known  
color matching functions.  
  
M - the conversion matrix  
 (n\_chromacy by n\_chromacy)  
  
Tsource - source color matching functions  
 (n\_chromacy by n\_wavelengths)  
Pdest - dest primaries spectral power distributions  
 (n\_chromacy by n\_wavelengths)  
  
### OPTIONAL  
source - source tristimulus vectors  
 (n\_chromacy by n\_lights)  
dest - destination tristimulus vectors  
 (n\_chromacy by n\_lights)  
  
8/2/94      dhb     Fixed variable name bug.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/M_TToP.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/M_TToP.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/M_TToP.m</code>
</div>

