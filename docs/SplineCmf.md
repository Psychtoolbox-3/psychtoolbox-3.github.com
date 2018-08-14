# [SplineCmf](SplineCmf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[T\_out] = [SplineCmf](SplineCmf)(wls\_in, T\_in, wls\_out, [extend])  
  
Convert the wavelength representation of a color matching functions/  
spectral sensitivities.  
  
Handling of out of range values:  
  extend == 0: Cubic spline, extends with zeros [default]  
  extend == 1: Cubic spline, extends with last value in that direction  
  extend == 2: Linear interpolation, linear extrapolation  
  
T\_in may have multiple rows, in which case T\_out does as well.  
  
wls\_in and wls\_out may be specified as a column vector of  
wavelengths or as a [start delta num] description.  
  
7/26/03 dhb  Add extend argument and pass to [SplineRaw](SplineRaw).  
8/22/05 pbg  Changed T\_out to include the extend variable (previously was  
             hardwired to "1".  
8/13/11 dhb  Update comment to reflect changes in [SplineRaw](SplineRaw).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/SplineCmf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/SplineCmf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/SplineCmf.m</code>
</div>

