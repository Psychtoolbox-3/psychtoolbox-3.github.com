# [UpdateAmbientSensor](UpdateAmbientSensor)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

cal = [UpdateAmbientSensor](UpdateAmbientSensor)(cal,new\_ambient\_sensor,[ADD])  
  
Update the ambient light used in the conversions.  The  
value for new\_ambient\_sensor should be passed in the  
same units as defined by T\_sensor in the call to  
[SetColorSpace](SetColorSpace).  
  
If flag ADD is true, passed ambient is added to current  
value.  Otherwise passed value replaces current value.  
ADD is false if not passed.  Use caution when setting ADD  
true -- if the ambient is changing during the experiment  
you typically don't want to keep adding multiple times.  
  
If instead you want to update in the measurement units,  
call [UpdateAmbient](UpdateAmbient) instead.  
  
7/7/98    dhb          Wrote it.  
4/5/02    dhb, ly  Update for new interface.  Internal names not changed.  
5/2/02    dhb, kr  Add ADD flag.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/UpdateAmbientSensor.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/UpdateAmbientSensor.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/UpdateAmbientSensor.m</code>
</div>

