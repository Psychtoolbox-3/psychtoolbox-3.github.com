# [LambNomogram](LambNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

T = [LambNomogram](LambNomogram)(S,lambdaMax)  
  
Compute spectral sensitivities according to the  
nomogram provided in Lamb, 1995, Vision Research,  
Vol. 35, pp. 3083-3091, equation 2'.  
  
The result is in quantal units, in the sense that to compute  
absorptions you want to incident spectra in quanta.  
To get sensitivity in energy units, apply [EnergyToQuanta](EnergyToQuanta)().  
  
Argument lambdaMax may be a column vector of wavelengths.  
  
8/20/98 dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/LambNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/LambNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/LambNomogram.m</code>
</div>

