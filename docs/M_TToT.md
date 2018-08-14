# [M_TToT](M_TToT)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[M] = M\_TToT(Tsource,Tdest)  
[M,dest] = M\_TToT(Tsource,Tdest,source)  
  
Compute the conversion matrix between two color  
spaces with known color matching functions.  
  
M - the conversion matrix  
 (n\_chromacy by n\_chromacy)  
  
Tsource - source color matching functions  
  (n\_wavelengths by n\_chromacy)  
Tdest - destination color matching functions  
  (n\_wavelengths by n\_chromacy)  
  
### OPTIONAL  
source - source tristimulus vectors  
 (n\_chromacy by n\_lights)  
dest - destination tristimulus vectors  
 (n\_chromacy by n\_lights)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/M_TToT.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/M_TToT.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/M_TToT.m</code>
</div>

