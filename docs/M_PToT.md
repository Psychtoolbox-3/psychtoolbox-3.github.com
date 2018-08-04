# [M_PToT](M_PToT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[M] = M\_PToT(Psource,Tdest)  
[M,dest] = M\_PToT(Psource,Tdest,source)  
  
Compute the conversion matrix between a color  
space with known primaries and one with known  
color matching functions.  
  
M - the conversion matrix  
 (n\_chromacy by n\_chromacy)  
  
Psource - source primaries spectral power distributions  
 (n\_chromacy by n\_wavelengths)  
Tdest - destination color matching functions  
 (n\_chromacy by n\_wavelengths)  
  
### OPTIONAL  
source - source tristimulus vectors  
 (n\_chromacy by n\_lights)  
dest - destination tristimulus vectors  
 (n\_chromacy by n\_lights)  
  
8/2/94      dhb     Fixed variable name bug.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/M_PToT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/M_PToT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/M_PToT.m</code>
</div>

