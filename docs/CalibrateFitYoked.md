# [CalibrateFitYoked](CalibrateFitYoked)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [CalibrateFitYoked](CalibrateFitYoked)(cal)  
  
Fit the gamma data from the yoked measurements.  
  
This has to do with Brainard lab HDR display calibration procedures  
and doesn't do anything unless some special fields exist  
in the calibration structure.  It's in the PTB because when we use  
it, we want to call it from script [RefitCalGamma](RefitCalGamma), and that one does  
belong in the PTB.    
  
4/30/10  dhb, kmo, ar  Wrote it.  
5/24/10  dhb           Update comment.  
5/25/10  dhb, ar       New input format.  
5/28/10  dhb, ar       Execute conditionally.  
6/10/10  dhb           Make sure returned gamma values in range an monotonic.  
5/26/12  dhb           Improve the comment so this is a little less weird.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CalibrateFitYoked.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CalibrateFitYoked.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CalibrateFitYoked.m</code>
</div>

