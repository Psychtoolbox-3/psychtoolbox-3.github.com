# [ISO2007MPECheckType1ContinuousRadiance](ISO2007MPECheckType1ContinuousRadiance)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)>[PsychISO2007MPE](PsychISO2007MPE)

[[IsOverLimit](IsOverLimit),[ISO2007MPEStruct](ISO2007MPEStruct)] = [ISO2007MPECheckType1ContinuousRadiance](ISO2007MPECheckType1ContinuousRadiance)(S\_in,radiancein\_WattsPerSrM2,stimulusDurationSecs,stimulusAreaDegrees2,eyeLengthMm)  
  
Run all the checks that apply to a radiance measurement for the ISO 2007 MPE standard, for a Type 1 instrument and continuous exposure.  
Does not do the convergent beam check -- see comment in Contents.m about when we think this applies.  
  
Returns a flag set to 1 if the input exceeds any of the limits, and a structure with the computed ISO2007MPE  
values and corresponding limits.  
  
We use 17 mm eye length by default.  You can override the eye length by passing a different length in mm.  
This value is used in the conversion from radiance to retinal irradiance.  
  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
IMPORTANT: Before using the ISO2007MPE routines, please see the notes on usage  
and responsibility in [PsychISO2007MPE](PsychISO2007MPE)/Contents.m (type "help [PsychISO2007MPE](PsychISO2007MPE)"  
at the Matlab prompt.  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
  
6/28/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPECheckType1ContinuousRadiance.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPECheckType1ContinuousRadiance.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPECheckType1ContinuousRadiance.m</code>
</div>

