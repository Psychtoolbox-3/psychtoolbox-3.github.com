# [M_PToP](M_PToP)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[M] = M\_PToP(Psource,Pdest,T)  
[M,dest] = M\_PToP(Psource,Pdest,T,source)  
  
Compute the conversion matrix between two color  
spaces with known primaries.  
The transformation requires a set of color matching  
functions to describe the observer.  
  
M - the conversion matrix  
 (n\_chromacy by n\_chromacy)  
  
Psource - source color primary spectral power distributions  
  (n\_wavelengths by n\_chromacy)  
Pdest - destination primary spectral power distributions  
  (n\_wavelengths by n\_chromacy)  
T - a set of color matching functions  
  (n\_chromacy by n\_wavelengths)  
  
### OPTIONAL  
source - source tristimulus vectors  
 (n\_chromacy by n\_lights)  
dest - destination tristimulus vectors  
 (n\_chromacy by n\_lights)  
  
8/2/94      dhb     Fixed bug in optional arg handling.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/M_PToP.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/M_PToP.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/M_PToP.m</code>
</div>

