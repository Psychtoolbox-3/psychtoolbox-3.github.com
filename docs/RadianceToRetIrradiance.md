# [RadianceToRetIrradiance](RadianceToRetIrradiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)>[Obsolete](Obsolete)

irradianceWattsPerUm2 = [RadianceToRetIrradiance](RadianceToRetIrradiance)(radianceWattsPerM2Sr,radianceS,pupilAreaMm2,eyeLengthMm)  
  
Perform the geometric calculations necessary to convert a measurement of source  
radiance to corresponding retinal irradiance.   
  
  Input radianceWattsPerM2Sr should be in units of power/m^2-sr-wlinterval.  
  Input radianceS gives the wavelength sampling information.  
  Input pupilAreaMm2 should be in units of mm^2.  
  Input eyeLengthMm should be the length of the eye in mm.  
  Output irradianceWattsPerUm2 is in units of power/um^2-wlinterval.  
  
  Light power may be expressed in watts or quanta-sec or in your  
  favorite units.  Indeed, it may also be passed as energy rather  
  than power.    
  
This conversion does not take absorption in the eye into account,  
as this is more conveniently foldeded into the spectral absorptance.  
  
See also: [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance), radPupilAreaFromLum, [EyeLength](EyeLength), [RetIrradianceToRadiance](RetIrradianceToRadiance).  
  
Note: This routine is now obsolete, as it mixes radiometric and unit conversions.  Preferred is to  
use [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance) and then take charge of your units in your  
calling code.  
  
7/10/03  dhb  Wrote it.  
11/06/03 dhb  Fixed comments about units, as per Lu Yin email.  
3/29/12  dhb  Comment on output units was wrong.  It said power/um^2-sec-wlinterval  
              but the 'sec' part makes no sense given the 'power' in the numerator.  
2/28/13  dhb  Make units clear in variable names.  
3/6/13   dhb  Rewrite to use new conversion function.  Move to Obsolete directory.  
         dhb  Also improved variable naming.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/Obsolete/RadianceToRetIrradiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/Obsolete/RadianceToRetIrradiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/Obsolete/RadianceToRetIrradiance.m</code>
</div>

