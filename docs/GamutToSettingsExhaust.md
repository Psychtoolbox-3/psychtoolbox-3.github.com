# [GamutToSettingsExhaust](GamutToSettingsExhaust)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

settings = [GamutToSettingsExhaust](GamutToSettingsExhaust)(gammaInput, gammaTable, gamut)  
  
Find the best device settings to produce  
the passed linear device coordinates.  
  
This version works by exhaustive search of the fit gamma table,  
and returns the value in that table that produces output closest  
to desired.  
  
The passed coordinates should be in the range [0,1].  
The returned settings also run from [0,1], but after  
inversion of the device's gamma measurements.  
  
5/26/12  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/GamutToSettingsExhaust.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/GamutToSettingsExhaust.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/GamutToSettingsExhaust.m</code>
</div>

