# [RadianceAndDegrees2ToCornIrradiance](RadianceAndDegrees2ToCornIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

cornealIrradiance\_PowerPerArea = [RadianceAndDegrees2ToCornIrradiance](RadianceAndDegrees2ToCornIrradiance)(radiance\_PowerPerSrArea,stimulusAreaDegrees2)  
  
Convert the radiance of a stimulus to corneal irradiance, given that we know the area of the stimulus in degrees2.  
The routine assumes that the stimulus is square with linear subtense sqrt(stimulusAreaDegrees2).  
  
Light power can be in your favorite units (Watts, quanta/sec) as can distance (m, cm, mm).  The units for  
area in the returned irradiance match those used for area in the passed radiance.  
  
So, if radiance is in Watts/[cm2-sr] then distance needs to be in cm and irradiance will be in Watts/cm2.  
  
This conversion, I believe, is correct for the case where the eye is viewing the surface along its  
surface normal, if we are thinking about a surface of fixed area.  For off axis viewing there will be  
a correction for the Lambertian dropoff in light with cos(theta).  This differs from computing retinal  
irradiance from radiance, where the area of the surface seen by a fixed retinal area increases exactly  
so as to compensate for that dropoff.  
  
The derivation also assumes the small angle approximation simulusSizeUnits = stimulusSizeRadians\*stimulusDistanceUnits,  
where units are the relavant units of length.  Although we don't have stimulusSizeUnits and stimulusDistanceUnits,  
these turn out to cancel out under the small angle approximation.  
  
See also: [RadianceAndDistanceAreaToCornIrradiance](RadianceAndDistanceAreaToCornIrradiance)  
  
2/20/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/RadianceAndDegrees2ToCornIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/RadianceAndDegrees2ToCornIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/RadianceAndDegrees2ToCornIrradiance.m</code>
</div>

