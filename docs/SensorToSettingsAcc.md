# [SensorToSettingsAcc](SensorToSettingsAcc)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

 [finalSettings,badIndex,quantized,perError,settings] = [SensorToSettingsAcc](SensorToSettingsAcc)(cal,sensor)  
  
 Convert from sensor color space coordinates to device  
 setting coordinates.  This routine makes use of the  
 full basis function information to compensate for spectral  
 shifts in the device primaries with input settings.  
  
 This depends on the standard calibration globals.  
  
 11/12/93   dhb      Wrote it.  
 3/30/94     dhb, jms Fixed logic bug in error computation.  
                      Return finalSettings as best during iteration  
 8/4/96     dhb      Update for stuff bag routines.  
 8/21/97    dhb      Update for structures.  
 3/10/98     dhb      Change nBasesOut to nPrimaryBases.  
 4/5/02     dhb, ly  New calling interface.  
 1/26/04    ly, dhb  Get rid of unused variable called "error".  
 11/22/09   dhb      Check basis dimension and do the simple fast thing if it is 1.  
                     This will speed things up when there is no point in trying the  
                     iterative algorithm.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/SensorToSettingsAcc.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/SensorToSettingsAcc.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/SensorToSettingsAcc.m</code>
</div>

