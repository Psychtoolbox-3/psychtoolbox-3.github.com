# [LumToRetIrradiance](LumToRetIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

irradiance = [RadianceToRetIrradiance](RadianceToRetIrradiance)(luminance,radiance,radianceS,pupilAreaMM,eyeSizeMM)  
  
Perform the geometric calculations necessary to convert a measurement of source  
radiance to corresponding retinal irradiance.   
  
  Input radiance should be in units of power/m^2-sr-wlinterval.  
  Input radianceS gives the wavelength sampling information.  
  Input pupilAreaMM should be in units of mm^2.  
  Input eyeSizeMM should be the length of the eye in mm.  
  Output irradiance is in units of power/um^2-sec-wlinterval.  
  
  Light power may be expressed in watts or quanta-sec or in your  
  favorite units.  Indeed, it may also be passed as energy rather  
  than power.    
  
This conversion does not take absorption in the eye into account,  
as this is more conveniently foldeded into the spectral absorptance.  
  
See also: [PupilAreaFromLum](PupilAreaFromLum), [IsomerizationsInEyeDemo](IsomerizationsInEyeDemo).  
  
7/10/03  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/LumToRetIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/LumToRetIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/LumToRetIrradiance.m</code>
</div>

