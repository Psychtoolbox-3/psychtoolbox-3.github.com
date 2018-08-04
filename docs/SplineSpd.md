# [SplineSpd](SplineSpd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[spd\_out] = [SplineSpd](SplineSpd)(wls\_in, spd\_in, wls\_out, [extend])  
  
Convert the wavelength representation of a spectral power distribution.  
Takes change of deltaLambda into account to keep matrix computations  
consistent across wavelength samplings.  
  
Handling of out of range values:  
  extend == 0: Cubic spline, extends with zeros [default]  
  extend == 1: Cubic spline, extends with last value in that direction  
  extend == 2: Linear interpolation, linear extrapolation  
  
spd\_in may have multiple columns, in which case spd\_out does as well.  
  
wls\_in and wls\_out may be specified as a column vector of  
wavelengths or as a [start delta n] description.  
  
If wls\_out is passed as a vector of wavelengths with just one sample, we don't   
know what the wavelength sampling is, and we can't do the conversion of  
power per wavelength band.  This condition is checked for and an error is  
thrown.  The fix is to pass the wavelengths as an S vector  
  S = [theWavelength wavelengthBandWidth 1].  
This forces an explicit value for the wavelength band width.  
  
5/6/98  dhb  Change normalization method so that sum is constant.  
             This is a little closer to the desired result for  
             functions with big derivatives.  
12/7/98 dhb  Remove 5/6/98 change, as it produces the wrong power  
             when you spline across different wavelength regions.  
7/26/03 dhb  Add extend argument and pass to [SplineRaw](SplineRaw).  
8/13/11 dhb  Update comment to reflect changes in [SplineRaw](SplineRaw).  
5/10/12 dhb  Small comment fix  
1/15/18 dhb  Can't believe I wrote this more than 20 years ago!  
        dhb  Put in error check for single wavelength value pass.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/SplineSpd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/SplineSpd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/SplineSpd.m</code>
</div>

