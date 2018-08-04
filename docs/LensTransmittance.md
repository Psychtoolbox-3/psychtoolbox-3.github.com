# [LensTransmittance](LensTransmittance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

[lensTransmit,lensDensity] = [LensTransmittance](LensTransmittance)(S,[species],[source],[ageInYears],[pupilDiameterMM])  
  
Return an estimate of the transmittance of the lens.  
  
Allowable species:  
  Human (Default)  
  
Allowable sources:  
  [StockmanSharpe](StockmanSharpe) (Default) - Stockman, Sharpe, & Fach (1999).  
  CIE                      - Formula from CIE 170-1:2006.  
  [WyszeckiStiles](WyszeckiStiles)           - W&S, Table 1(2.4.6), p. 109.  First data set in table.  
  None                     - Unity transmittance.  
  
The answer is returned in a row vector.  This function  
depends on data contained in directory  
[PsychColorimetricData](PsychColorimetricData):[PsychColorimetricMatFiles](PsychColorimetricMatFiles).  
  
The CIE source will take age in years and pupil size in mm.  
The default age is 32.  The acceptable range is 20-80.  
The default pupil size is 3 mm.  Sizes less than 3 are treated  
as 3.  Sizes greater than 7 are treated as 7.  The interpolation  
between 3 and 7 doesn't appear to be part of the standard but  
I coded it in anyway.  
  
  
7/8/03  dhb  Made this a separate function.  
7/11/03 dhb  Species arg, change name.  
7/23/03 dhb  Add Stockman estimate.  
7/26/03 dhb  Extend functions, rather than zero truncate.  
8/12/11 dhb  Start to write CIE version.  Return lensDensity too.  
        dhb  Finish. Add pupil size.  
8/13/11 dhb  Linearly extrapolate read functions outside of range.  
9/17/12 dhb  Return density for 'None' case as well.  
8/9/13  dhb  More consistent returning of density for 'None' case.  
8/11/13 dhb  Try to make dimensions of returned density match those of returned transmittance.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/LensTransmittance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/LensTransmittance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/LensTransmittance.m</code>
</div>

