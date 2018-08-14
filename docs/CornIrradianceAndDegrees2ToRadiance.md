# [CornIrradianceAndDegrees2ToRadiance](CornIrradianceAndDegrees2ToRadiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

radiance\_PowerPerSrArea = [CornIrradianceAndDegrees2ToRadiance](CornIrradianceAndDegrees2ToRadiance)(cornealIrradiance\_PowerPerArea,stimulusAreaDegrees2)  
  
Convert the corneal irradiance of a stimulus to radiance, given that we know the area of the stimulus in degrees2.  
The routine assumes that the stimulus is rectangular with linear subtense sqrt(stimulusAreaDegrees2).  
  
Light power can be in your favorite units (Watts, quanta/sec) as can distance (m, cm, mm).  The units for  
area in the returned radiance match those used for area in the passed irradiance.  So, if irrradiance is in Watts/cm2  
the radiance will be in Watts/[cm2-sr].  
  
The derivation assumes the small angle approximation simulusSizeUnits = stimulusSizeRadians\*stimulusDistanceUnits,  
where units are the relavant units of length.  Although we don't have stimulusSizeUnits and stimulusDistanceUnits,  
these turn out to cancel out under the small angle approximation.  
  
See also: [RadianceAndDistanceAreaToCornIrradiance](RadianceAndDistanceAreaToCornIrradiance), [RadianceAndDegrees2ToCornIrradiance](RadianceAndDegrees2ToCornIrradiance)  
  
2/22/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/CornIrradianceAndDegrees2ToRadiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/CornIrradianceAndDegrees2ToRadiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/CornIrradianceAndDegrees2ToRadiance.m</code>
</div>

