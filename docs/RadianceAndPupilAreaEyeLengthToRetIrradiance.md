# [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

retIrradiance\_PowerPerArea = [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance)(radiance\_PowerPerAreaSr,radianceS,pupilArea,eyeLength)  
  
Perform the geometric calculations necessary to convert a measurement of source  
radiance to corresponding retinal irradiance.   
  
Let x be the units of distance (m, cm, mm, um, etc.)  
  
  Input radiance\_PowerPerAreaSr should be in units of power/x^2-sr-wlinterval.  
  Input radianceS gives the wavelength sampling information (nm).  
  Input pupilArea should be in units of x^2.  
  Input eyeLength should be the length of the eye in units of x  
  
  Output retIrradiance\_PowerPerArea is in units of power/x^2-wlinterval.  
  
  Light power may be expressed in watts or quanta-sec or in your  
  favorite units.  Indeed, it may also be passed as energy rather  
  than power.    
  
This conversion does not take absorption in the eye into account,  
as this is more conveniently foldeded into the spectral absorptance.  
  
The wavelength sampling is not needed or used, and the world would be a  
better place if it were not passed.  But taking it out of the arg list  
now would probably break a number of calling programs in an irritating  
manner.  
  
See also: [PsychRadiometric](PsychRadiometric), [RetIrradianceAndPupilAreaEyeLengthToRadiance](RetIrradianceAndPupilAreaEyeLengthToRadiance), [PupilAreaFromLum](PupilAreaFromLum), [EyeLength](EyeLength).  
  
3/6/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/RadianceAndPupilAreaEyeLengthToRetIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/RadianceAndPupilAreaEyeLengthToRetIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/RadianceAndPupilAreaEyeLengthToRetIrradiance.m</code>
</div>

