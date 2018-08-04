# [RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea](RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

retIrradiance\_PerArea = [RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea](RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea)(retIrradiance\_PerDegrees2,eyeLength)  
  
Convert retinal irradiance measured in units of Y/deg^2 to units of  
Y/x^2, where x is a unit of distance (m, cm, mm, um, etc.) and  
Y is a measure of light amount (Watts, Joules, quanta/sec, quanta, etc.)  
  
Eye length should be passed in units of x.  
  
The conversion assumes that we are in the small angle regime, where  
degrees are essentially linear with retinal extent.  
  
See also: [PsychRadiometric](PsychRadiometric), [RetIrradiancePerAreaAndEyeLengthToRetIrradiancePerDegrees2](RetIrradiancePerAreaAndEyeLengthToRetIrradiancePerDegrees2).  
  
6/23/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea.m</code>
</div>

