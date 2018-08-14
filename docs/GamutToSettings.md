# [GamutToSettings](GamutToSettings)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

settings = [GamutToSettings](GamutToSettings)(cal, gamut)  
  
Find the best device settings to produce  
the passed linear device coordinates.  
  
The passed coordinates should be in the range [0,1].  
The returned settings also run from [0,1], but after  
inversion of the device's gamma measurements.  
  
The returned argument values is what you actually should  
get after quantization error.  
  
9/26/93    dhb   Added calData argument.  
10/19/93   dhb   Allow gamma table dimensions to exceed device settings.  
11/11/93   dhb   Update for new calData routines.  
8/4/96     dhb   Update for stuff bag routines.  
8/21/97    dhb   Update for structures.  
4/13/02  awi   Replaced [SettingsToDevice](SettingsToDevice) with new name [SettingsToPrimary](SettingsToPrimary).  
11/16/06   dhb   Adjust for [0,1] world.  Involves changing what's passed  
                 in and out  
5/26/12    dhb   Add gammaMode == 2 case.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/GamutToSettings.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/GamutToSettings.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/GamutToSettings.m</code>
</div>

