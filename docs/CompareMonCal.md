# [CompareMonCal](CompareMonCal)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

isSame = [CompareMonCal](CompareMonCal)(cal1,cal2,[IGNOREDATE])  
  
Checks if the two calibrations are the same.  Useful  
for preventing blunders if you have programs that  
precompute and save quantities based on monitor calibrations.  
In that case, this can be used to ensure that current   
calibration matches the one used to do the pre-computing.  
  
Checks date/time, screen, and computer.  Could check the  
actual data, but that seems like overkill.  
  
9/17/97  pbe       Wrote it.   
9/18/97  pbe, dhb  Modify interface, change name.  
1/16/98  dhb       Add any around string compares, necessary for desired effect.  
1/21/98  dhb       Add IGNOREDATE flag.  
3/10/98  dhb         Change name to [CompareMonCal](CompareMonCal).  
7/3/98   dhb, pbe  Change for cal.describe format.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/CompareMonCal.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/CompareMonCal.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/CompareMonCal.m</code>
</div>

