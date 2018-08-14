# [GamutToSettingsTbl](GamutToSettingsTbl)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[settings] = [GamutToSettingsTbl](GamutToSettingsTbl)(iGammaTable,gamut)  
  
Find the best integer device settings to produce  
the passed linear device coordinates. Use a precomputed  
inverse gamma table.  
  
The passed coordinates should be in the range [0,1].  
The returned values run from [0,nlevels-1], where nlevels  
is the number of quantized levels available on the device.  
  
1/21/95     dhb     Wrote it.  
5/26/12       dhb     Remove reference in comments to a return value that does not exist.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/GamutToSettingsTbl.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/GamutToSettingsTbl.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/GamutToSettingsTbl.m</code>
</div>

