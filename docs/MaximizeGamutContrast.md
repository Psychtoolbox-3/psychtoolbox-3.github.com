# [MaximizeGamutContrast](MaximizeGamutContrast)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[s,sPos,sNeg] = [MaximizeGamutContrast](MaximizeGamutContrast)(dir,white)  
  
Find the scalar that maximizes the contrast around  
the white point.  Input should be specified in device  
primary coordinates.  
  
2/22/94  dhb    Wrote it.  
4/3/94   dhb    Analytic version.  
4/4/94   dhb    Avoid divide by zero problem.  
8/17/94  dhb    Handle small values of useWhite.  
8/23/94  dhb    Fix 8/17 fix to handle negative numbers.  Sigh.  
2/16/98  dgp    Renamed from [MaxGmtCon](MaxGmtCon) to [MaximizeGamutContrast](MaximizeGamutContrast).  
12/3/98  dhb    Add directional return values.  
         dhb    Remove redundant calculations.  
9/7/00   mpr    Made zero handling code more compact; did away with unnecessary variable.  
1/31/10  dhb    Range check on input white point.  
         dhb    Remove calls to find as per MATLAB lint checker.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/MaximizeGamutContrast.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/MaximizeGamutContrast.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/MaximizeGamutContrast.m</code>
</div>

