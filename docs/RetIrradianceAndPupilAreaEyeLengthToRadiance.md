# [RetIrradianceAndPupilAreaEyeLengthToRadiance](RetIrradianceAndPupilAreaEyeLengthToRadiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

radiance\_PowerPerAreaSr = [RetIrradianceAndPupilAreaEyeLengthToRadiance](RetIrradianceAndPupilAreaEyeLengthToRadiance)(irradiance\_PowerPerArea,irradianceS,pupilArea,eyeLength)  
  
Perform the geometric calculations necessary to convert a measurement of retinal  
irradiance to the source radiance that would produce it.  
  
Perform the geometric calculations necessary to convert a measurement of source  
radiance to corresponding retinal irradiance.   
  
Let x be the units of distance (m, cm, mm, um, etc.)  
  
  Input irradiance\_PowerPerArea is in units of power/x^2-wlinterval.  
  Input irradianceS gives the wavelength sampling information.  
  Input pupilArea should be in units of x^2.  
  Input eyeLength should be the length of the eye in x.  
  
  Output radiance\_PowerPerAreaSr is in units of power/x^2-sr-wlinterval.  
  
  Light power may be expressed in watts or quanta-sec or in your  
  favorite units.  Indeed, it may also be passed as energy rather  
  than power.    
  
This conversion does not take absorption in the eye into account,  
as this is more conveniently foldeded into the spectral absorptance.  
  
See also: [PsychRadiometric](PsychRadiometric), [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance), [PupilAreaFromLum](PupilAreaFromLum), [EyeLength](EyeLength).  
  
3/6/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/RetIrradianceAndPupilAreaEyeLengthToRadiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/RetIrradianceAndPupilAreaEyeLengthToRadiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/RetIrradianceAndPupilAreaEyeLengthToRadiance.m</code>
</div>

