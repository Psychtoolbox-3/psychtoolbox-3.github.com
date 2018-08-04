# [PsychRadiometric](PsychRadiometric)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)

Psychtoolbox:[PsychRadiometric](PsychRadiometric).  
  
Radiometric and photometric calculations.  See also the closely related  
Psychtoolbox:[PsychColorimetric](PsychColorimetric) and its related data folders.  Sometimes  
it is not entirely clear whether a routine is better classified as  
radiometric or colorimetric. Apologies if our intuitions don't match  
yours.  
  
  
  [EnergyToQuanta](EnergyToQuanta)      - Convert monochromatic energy to quanta.  
  [CornIrradianceAndDegrees2ToRadiance](CornIrradianceAndDegrees2ToRadiance) - Convert corneal irradiance to radiance, given stimulus area in degrees^2.  
  [FrequencyTHzToWavelengthNm](FrequencyTHzToWavelengthNm) - Convert wavelength of light (nm) to frequency [(THz)]((THz)).  
  [PowerToTrolands](PowerToTrolands)     - Convert monochromatic power to photopic trolands.  
  [PsychAnsiZ136MPE](PsychAnsiZ136MPE)    - Ansi 136.1-2007 standard for maximum permissible light exposure.  
  [PsychISO2007MPE](PsychISO2007MPE)     - ISO 2007 standard for maximum permissible light exposure  
  [QuantaToEnergy](QuantaToEnergy)      - Convert monochromatic quanta to energy.  
  [QuantaToTrolands](QuantaToTrolands)    - Convert monochromatic quanta to photopic trolands.  
  [RadianceAndDegrees2ToCornIrradiance](RadianceAndDegrees2ToCornIrradiance) - Convert radiance to corneal irradiance, given stimulus area in degrees^2.  
  [RadianceAndDistanceAreaToCornIrradiance](RadianceAndDistanceAreaToCornIrradiance) - Convert radiance to corneal irradiance, given stimulus area and distance in linear units (e.g, cm).  
  [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance) - Convert radiance to retinal irradiance, given pupil area and eye length.  
  [RadiometricConversionsTest](RadiometricConversionsTest) - Test some of the radiometric conversion routines.  
  [RetIrradianceAndPupilAreaEyeLengthToRadiance](RetIrradianceAndPupilAreaEyeLengthToRadiance) - Convert retinal irradiance to radiance, given pupil area and eye length.  
  [RetIrradiancePerAreaAndEyeLengthToRetIrradiancePerDegrees2](RetIrradiancePerAreaAndEyeLengthToRetIrradiancePerDegrees2) - Convert retinal irradiance per area to retinal irradiance per degrees2.  
  [RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea](RetIrradiancePerDegrees2AndEyeLengthToRetIrradiancePerArea) - Convert retinal irradiance per degrees2 to retinal irradiance per area.  
  [RetIrradianceToTrolands](RetIrradianceToTrolands) - Convert retinal irradiance (power units) to trolands.  
  [TrolandsToLum](TrolandsToLum)       - Convert trolands to luminance (cd/m2).  
  [TrolandsToPower](TrolandsToPower)     - Convert monochromatic photopic trolands to power.  
  [TrolandsToQuanta](TrolandsToQuanta)    - Convert monochromatic photopic trolands to quanta.  
  [TrolandsToRetIrradiance](TrolandsToRetIrradiance) - Get retinal irradiance (power units) from spectrum and trolands.  
  [WattsToRetIrradiance](WattsToRetIrradiance) - Get absolute retinal irradiance (power units) from rel. spectrum and watts/area.  
  [WavelengthNmToFrequencyTHz](WavelengthNmToFrequencyTHz) - Convert frequency of light [(THz)]((THz)) to wavelength (nm).  
  
Obsolete  
  The routines below use specific unit conventions.  I now think it is better not to mix unit conversions  
  in so intimately with radiometric conversions.  These routines have been reimplemented to call   
  the newer more unit free versions, but since they are used throughout various user programs are  
  kept here for now.  Someday we may decide to make them go away.  
  
  [RadianceToRetIrradiance](RadianceToRetIrradiance) - See [RadianceAndPupilAreaEyeLengthToRetIrradiance](RadianceAndPupilAreaEyeLengthToRetIrradiance).  
  [RetIrradianceToRadiance](RetIrradianceToRadiance) -   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/Contents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/Contents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/Contents.m</code>
</div>

{{category}}