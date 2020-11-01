# [MeasXYZ](MeasXYZ)
##### >[Psychtoolbox](Psychtoolbox)>[PsychHardware](PsychHardware)

[XYZ, qual] = [MeasXYZ](MeasXYZ)([meterType=1])  
  
Measures XYZ tristimulus coordinates, luminance in  
cd/m^2.  
  
  meterType 1 is the PR650 (default)  
  meterType 2 is the CVI (need [CVIToolbox)](CVIToolbox)) - Not yet implemented!  
  meterType 3 is the CRS Colorimeter  
  meterType 4 is the PR655  
  meterType 5 is the PR670  
  meterType 6 is the PR705 - Not yet implemented!  
  meterType 7 is the CRS [ColorCal2](ColorCal2).  
  
  
Returns XYZ tristimulus coordinates in 'XYZ'.  
Returns quality code in 'qual': 0 = Ok. Other numbers mean trouble, e.g., -8  
means "low light" ie. insufficient precision on some devices like the PR-xxx's.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychHardware/MeasXYZ.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychHardware/MeasXYZ.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychHardware/MeasXYZ.m</code>
</div>

