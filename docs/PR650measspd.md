# [PR650measspd](PR650measspd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)>[PR650Toolbox](PR650Toolbox)

[spd,qual] = [PR650measspd](PR650measspd)(S,[syncMode])  
  
Make a measurement of the spectrum.  Tries to be smart  
about using sync or not, unless it is turned off by  
passed variable.  
  
syncMode = 'on':  Try to sync integration time with display.  Retry without if it fails. (default)  
syncMode = 'off': Don't try to sync.  
  
8/26/10  dhb  Add DEBUG option to figure out why this dies sometimes.  
3/8/11   dhb  Pass syncMode option to speed things up for displays where it doesn't work.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/PR650Toolbox/PR650measspd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/PR650Toolbox/PR650measspd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/PR650Toolbox/PR650measspd.m</code>
</div>

