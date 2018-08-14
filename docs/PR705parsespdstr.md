# [PR705parsespdstr](PR705parsespdstr)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR705Toolbox](PR705Toolbox)

[PR705parsespdstr](PR705parsespdstr) - Parses the spectral power distribution string returned by the PR-705.  
  
Syntax:  
spd = [PR705parsespdstr](PR705parsespdstr)(rawspd [, S])  
  
Description:  
Parse the spectral power distribution string returned by the PR-705. The  
results are splined to the desired wavelength sampling defined by the 'S'  
input parameter.  
  
Input:  
rawspd (1xN char) - Raw data returned from a meter measurment.  
S (1x3) - Wavelength sampling.  Default: [380 5 81]  
  
12/06/12    zlb   Wrote it based on the [PR670Toolbox](PR670Toolbox).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705parsespdstr.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR705Toolbox/PR705parsespdstr.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR705Toolbox/PR705parsespdstr.m</code>
</div>

