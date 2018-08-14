# [SplineSrf](SplineSrf)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[srf\_out] = [SplineSrf](SplineSrf)(wls\_in, srf\_in, wls\_out, [extend])  
  
Convert the wavelength representation of a surface reflectance function.  
  
  
Handling of out of range values:  
  extend == 0: Cubic spline, extends with zeros [default]  
  extend == 1: Cubic spline, extends with last value in that direction  
  extend == 2: Linear interpolation, linear extrapolation  
  
srf\_in may have multiple columns, in which case srf\_out does as well.  
  
wls\_in and wls\_out may be specified as a column vector of  
wavelengths or as a [start delta num] description.  
  
7/26/03 dhb  Add extend argument and pass to [SplineRaw](SplineRaw).  
8/13/11 dhb  Update comment to reflect changes in [SplineRaw](SplineRaw).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/SplineSrf.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/SplineSrf.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/SplineSrf.m</code>
</div>

