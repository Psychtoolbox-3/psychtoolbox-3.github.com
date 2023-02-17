# [CV1Test](CV1Test)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PsychVRToolbox](PsychVRToolbox)

res = [CV1Test](CV1Test)([waitframes=90][, useRTbox=0]) - A timing test script for [HMDs](HMDs) by use of a photometer.  
  
Needs the [RTBox](RTBox), and a photo-diode or such, e.g., a [ColorCal](ColorCal)-II,  
connected to the TTL trigger input.  
  
Atm., we still measure a discrepancy of about 75 msecs between what  
'[Flip](Flip)' reports according to our drivers timestamping, and what the  
photometer based timestamping reports. That's still not good enough, and  
i'm out of ideas on how to improve this.  
  
Onset scheduling also becomes erratic for short waitframes intervals  
between white flashes.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PsychVRToolbox/CV1Test.m</code>
</div>

