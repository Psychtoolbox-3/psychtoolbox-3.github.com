# [DawisNomogram](DawisNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[T\_absorbance] = [DawisNomogram](DawisNomogram)(S,lambdaMax)  
  
Compute normalized absorbance according to the  
nomogram provided in Dawis, 1981, Vision Research,  
Vol. 21, pp. 1427-1430.  
  
T\_absorbance contains the absorbance.  
This is specified according to the CVRL web page  
definition absorbance = log(I\_incident/I\_transmitted),  
so the numbers are all positive.  The peak is normalized  
to one.  
  
For low density, the absorbance has the same shape as  
the spectral senstivity.  
  
The nomogram is shifted along the wavelength axis  
using a multiplicative rather than additive procedure.  
  
The result is in quantal units, in the sense that to compute  
absorptions you want to incident spectra in quanta.  
To get sensitivity in energy units, apply [EnergyToQuanta](EnergyToQuanta)().  
  
Argument lambdaMax may be a column vector of wavelengths.  
  
10/30/97 dhb  Wrote it.  
07/01/03 dhb  Add computation of T\_absorbance.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/DawisNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/DawisNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/DawisNomogram.m</code>
</div>

