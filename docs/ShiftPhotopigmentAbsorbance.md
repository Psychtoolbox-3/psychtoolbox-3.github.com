# [ShiftPhotopigmentAbsorbance](ShiftPhotopigmentAbsorbance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetricData](PsychColorimetricData)

absorbance = [ShiftPhotopigmentAbsorbance](ShiftPhotopigmentAbsorbance)(S,absorbance,lambdaMaxShift,shiftMode)  
  
Function to shift photopigment absorbances.  Probably a reasonable  
approximation to biological reality for small shifts of lambda max.  
  
There are two ways of shifting photopigment absorbances:  
'linear' - default  
  Shifts the photopigment absorbance on a linear wavelength axis.  This  
  is what Asano, Fairchild, & Bonde (2016), PLOS One, doi:  
  10.1371/journal.pone.0145671 do.  
  
'log'  
  Shift the photopigment absorbance along a log wavelength axis to give it  
  a new lambda max.  This is the way Lamb (1995) suggested would lead to a  
  close approximation of biological shifts in photopigment lambda-max.  
  
Linearly extrapolates as necessary to preserve wavelength sampling of  
input.  
  
2/8/16  dhb, ms  Wrote it.  
2/10/16 dhb, ms  Do shifting on a fine (0.25 nm) wavelength spacing.  
2/12/16 ms       Implement linear and log shifting.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetricData/ShiftPhotopigmentAbsorbance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetricData/ShiftPhotopigmentAbsorbance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetricData/ShiftPhotopigmentAbsorbance.m</code>
</div>

