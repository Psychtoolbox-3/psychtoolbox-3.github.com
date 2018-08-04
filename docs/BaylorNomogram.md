# [BaylorNomogram](BaylorNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

T = [BaylorNomogram](BaylorNomogram)(S,lambdaMax)  
  
Compute spectral sensitivities according to the  
nomogram provided in Baylor, Nunn, and Schnapf, 1987.  
  
The result is in quantal units, in the sense that to compute  
absorptions you want to incident spectra in quanta.  
To get sensitivity in energy units, apply [EnergyToQuanta](EnergyToQuanta)().  
  
Argument lambdaMax may be a column vector of wavelengths.  
  
6/22/96  dhb  Wrote it.  
10/16/97 dhb  Add comment about energy units.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/BaylorNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/BaylorNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/BaylorNomogram.m</code>
</div>

