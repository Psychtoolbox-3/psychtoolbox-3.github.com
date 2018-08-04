# [PR670parsespdstr](PR670parsespdstr)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR670Toolbox](PR670Toolbox)

[PR670parsespdstr](PR670parsespdstr) - Parses the  spectral power distribution string returned by the PR-670.  
  
Syntax:  
spd = [PR670parsespdstr](PR670parsespdstr)(readStr)  
spd = [PR670parsespdstr](PR670parsespdstr)(readStr, S);  
  
Description:  
Parse the spectral power distribution string returned by the PR-670.  The  
results are splined to the desired wavelength sampling defined by the 'S'  
input parameter.  
  
Input:  
readStr (1xN char) - Raw data returned from a meter measurment.  
S (1x3) - Wavelength sampling.  Default: [380 5 81]  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR670Toolbox/PR670parsespdstr.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR670Toolbox/PR670parsespdstr.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR670Toolbox/PR670parsespdstr.m</code>
</div>

