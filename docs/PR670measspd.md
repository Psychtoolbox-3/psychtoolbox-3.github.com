# [PR670measspd](PR670measspd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR670Toolbox](PR670Toolbox)

[PR670measspd](PR670measspd) - Make a measurement measurement.  
  
Syntax:  
[spd, qual] = [PR670measspd](PR670measspd)(S)  
[spd, qual] = [PR670measspd](PR670measspd)(S, syncMode)  
  
Input:  
S (1x3) - Desired wavelength sampling. Default: [380 5 81]  
syncMode (string) - Toggles syncronization with the light source.  Set  
    using the strings 'on' or 'off'.  Default: 'on'  
  
Output:  
spd (Mx1) - Light source spectrum.  
qual (scalar) - Measurement quality code.  See the PR-670 manual.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR670Toolbox/PR670measspd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR670Toolbox/PR670measspd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR670Toolbox/PR670measspd.m</code>
</div>

