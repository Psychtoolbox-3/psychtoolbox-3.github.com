# [RadianceAndDistanceAreaToCornIrradiance](RadianceAndDistanceAreaToCornIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

cornealIrradiance\_PowerPerArea = [RadianceAndDistanceAreaToCornIrradiance](RadianceAndDistanceAreaToCornIrradiance)(radiance\_PowerPerSrArea,stimulusDistance,stimulusArea)  
  
Convert the radiance of a stimulus to corneal irradiance, given that we know the distance to the stimulus and the area  
of the stimulus.  Light power can be in your favorite units (Watts, quanta/sec) as can distance (m, cm, mm).  Area  
needs to be in units that are the square of your distance units, both for the radiance passed and the stimulus area  
passed. So, if radiance is in Watts/[cm2-sr] then distance needs to be in cm and irradiance will be in Watts/cm2.  
  
This conversion, I believe, is correct for the case where the eye is viewing the surface along its  
surface normal, if we are thinking about a surface of fixed area.  For off axis viewing there will be  
a correction for the Lambertian dropoff in light with cos(theta).  This differs from computing retinal  
irradiance from radiance, where the area of the surface seen by a fixed retinal area increases exactly  
so as to compensate for that dropoff.  
  
See also: [RadianceAndDegrees2ToCornIrradiance](RadianceAndDegrees2ToCornIrradiance), [CornIrradianceAndDegrees2ToRadiance](CornIrradianceAndDegrees2ToRadiance)  
  
2/20/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/RadianceAndDistanceAreaToCornIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/RadianceAndDistanceAreaToCornIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/RadianceAndDistanceAreaToCornIrradiance.m</code>
</div>

