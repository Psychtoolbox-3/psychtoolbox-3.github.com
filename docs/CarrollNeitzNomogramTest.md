# [CarrollNeitzNomogramTest](CarrollNeitzNomogramTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

maxAbsDiff = [CarrollNeitzNomogramTest](CarrollNeitzNomogramTest)  
  
Validate [CarrollNeitzNomogram](CarrollNeitzNomogram) against the original Neitz-lab spectsens.m.  
  
The PTB nomogram returns absorbance normalized to a peak of 1. The  
original spectsens helper returns absorptance with optical density and  
a normalization by the peak absorptance, 1-10^-OD. To compare like with  
like, we:  
  1) compute PTB absorbance with [CarrollNeitzNomogram](CarrollNeitzNomogram);  
  2) convert to absorptance with [AbsorbanceToAbsorptance](AbsorbanceToAbsorptance);  
  3) normalize by the peak absorptance to match spectsens;  
  4) normalize the sampled spectsens result to peak 1, matching the PTB  
     convention applied inside [CarrollNeitzNomogram](CarrollNeitzNomogram) when S(2) <= 1.  
  
The test plots one panel each for the L, M, and S cones and reports the  
maximum absolute difference across all wavelengths and cone classes.  
  
History:  
  2026-04-10  dhb    Wrote it.  
  2026-04-10  Codex  Implement validation against original spectsens.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogramTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogramTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogramTest.m</code>
</div>

