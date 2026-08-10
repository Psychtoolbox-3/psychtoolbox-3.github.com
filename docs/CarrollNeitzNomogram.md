# [CarrollNeitzNomogram](CarrollNeitzNomogram)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

T\_absorbance = [CarrollNeitzNomogram](CarrollNeitzNomogram)(S, lambdaMax)  
  
Compute normalized absorbance according to the nomogram of  
Carroll, [McMahon](McMahon), Neitz, & Neitz (2000), J. Opt. Soc. Am. A, 17(3), 499-509.  
  
T\_absorbance contains the absorbance (not log absorbance).  
The CVRL convention is used: absorbance = log(I\_incident/I\_transmitted),  
so values are positive, with a peak of 1.  The peak is normalized  
explicitly to 1 when wavelength spacing S(2) <= 1 nm.  
  
The result is in quantal units.  To get sensitivity in energy units,  
apply [EnergyToQuanta](EnergyToQuanta)().  
  
Argument lambdaMax may be a column vector of lambda max values, in which  
case T\_absorbance is nLambdaMax x nWls.  
  
The nomogram is parameterized relative to a reference lambda max of  
558.5 nm.  The internal shifted frequency variable is  
  x = lambdaMax / (558.5 \* wl)  
which is analogous to the ratio form used by the Govardovskii nomogram.  
  
Reasonable lambda max values for (L, M, S): 557.5, 530, 420 nm.  
These values are from Neitz & Neitz (2011), who report good agreement  
between this template and CIE cone fundamentals derived from color matching  
at these peaks; see their Figure 3 and surrounding text.  
  Neitz, J. & Neitz, M. (2011). The genetics of normal and defective  
  color vision. Vision Research, 51, 633-651.  
  
See also [CarrollNeitzNomogramTest](CarrollNeitzNomogramTest), [PhotpigmentNomogramDemo](PhotpigmentNomogramDemo).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogram.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogram.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/CarrollNeitzNomogram.m</code>
</div>

