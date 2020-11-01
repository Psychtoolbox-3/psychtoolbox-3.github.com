# [MeasMonXYZ](MeasMonXYZ)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

XYZ = [MeasMonXYZ](MeasMonXYZ)(window, settings [, whichMeterType=1])  
  
Measure the XYZ of a series of monitor settings.  
  
### Usage:  
  
'window' Onscreen window handle for window to present into.  
'settings' a 3-rows by nMeas columns matrix with each column defining one  
[r,g,b]' color value to measure.  
  
### 'whichMeterType' type of Colorimeter to use:  
  
  0 - Return random spectra. This is useful for testing when you don't have a meter.  
\> 0 - Use [MeasXYZ](MeasXYZ)(whichMeterType) to measure. See "help [MeasXYZ](MeasXYZ)" for available meter types.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/MeasMonXYZ.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/MeasMonXYZ.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/MeasMonXYZ.m</code>
</div>

