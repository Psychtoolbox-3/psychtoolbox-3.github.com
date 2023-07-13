# [MeasMonSpd](MeasMonSpd)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

[spd,S] = [MeasMonSpd](MeasMonSpd)(window, settings, [S], [syncMode], [whichMeterType], [theClut])  
  
Measure the Spd of a series of monitor settings.  
  
This routine is specific to go with [CalibrateMon](CalibrateMon),  
as it depends on the action of [SetMon](SetMon).   
  
If whichMeterType is passed and set to 0, then the routine  
returns random spectra.  This is useful for testing when  
you don't have a meter.  
  
Other valid types: See list in 'help CMCheckInit' for various Photo Research  
PR-xxx colormeters.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/MeasMonSpd.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/MeasMonSpd.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/MeasMonSpd.m</code>
</div>

