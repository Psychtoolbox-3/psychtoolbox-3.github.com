# [SetGammaMethod](SetGammaMethod)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [SetGammaMethod](SetGammaMethod)(cal,gammaMode,[precision])  
  
Set up the gamma correction mode to be used.  Options  
are:  
  gammaMode == 0 - search table using linear interpolation via interp1.  
  gammaMode == 1 - inverse table lookup.  Fast but less accurate.  
  gammaMode == 2 - exhaustive search  
  
If gammaMode == 1, then you may specify the precision of the  
inverse table.  The default is 1000 levels.  
  
See also [RefitCalGamma](RefitCalGamma), [CalibrateFitGamma](CalibrateFitGamma), [GamutToSettings](GamutToSettings)  
  
8/4/96  dhb  Wrote it.  
8/21/97 dhb  Update for structure.  
3/12/98 dhb  Change name to [SetGammaCorrectMode](SetGammaCorrectMode)  
5/26/12 dhb  Add real exhaustive search mode (2).   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/SetGammaMethod.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/SetGammaMethod.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/SetGammaMethod.m</code>
</div>

