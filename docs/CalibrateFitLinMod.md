# [CalibrateFitLinMod](CalibrateFitLinMod)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [CalibrateFitLinMod](CalibrateFitLinMod)(cal)  
  
Fit the linear model to spectral calibration data.  
  
3/26/02  dhb  Pulled out of [CalibrateMonDrvr](CalibrateMonDrvr).  
3/27/02  dhb  Add case of nPrimaryBases == 0.  
2/15/10  dhb  Fix so that first basis vector is good approximation to max  
              input primary spectrum.  
         dhb  Normalize basis vectors so that their max power matches that   
              of first component.  
4/30/10  dhb  Execute yoked fit if yokedGamma flag is set.  
5/25/10  dhb, ar Change yoked field names to match  
5/26/10  dhb, ar Still fussing with names.  
5/28/10  dhb, ar Pull out yoked fitting from here -- too confusing.  
5/27/12  dhb     Handle case where there are more measurements than wavelength samples.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CalibrateFitLinMod.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CalibrateFitLinMod.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CalibrateFitLinMod.m</code>
</div>

