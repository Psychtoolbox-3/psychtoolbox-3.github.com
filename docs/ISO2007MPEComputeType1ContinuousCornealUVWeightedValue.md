# [ISO2007MPEComputeType1ContinuousCornealUVWeightedValue](ISO2007MPEComputeType1ContinuousCornealUVWeightedValue)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)>[PsychISO2007MPE](PsychISO2007MPE)

[val\_UWattsPerCm2,limit\_UWattsPerCm2] = [ISO2007MPEComputeType1ContinuousCornealUVWeightedValue](ISO2007MPEComputeType1ContinuousCornealUVWeightedValue)(S,radiance\_WattsPerSrM2,weightingS,stimulusDurationSecs,stimulusAreaDegrees2)  
  
Compute the weighted UV radiation for Type 1 instruments as given on page 7, Table 2,   
5.4.1.1.  
  
Input spectrum is radiance in units of Watts/[sr-m2-wlinterval].  
  
Also return the exposure limit for this quantity.  
  
See page 6 for a definition of a Type 1 instrument.  As far as I can tell, the key  
criterion is that it doesn't put out more light that exceeds the Type 1 limits.  
  
If the exposure time is longer than 2 hours the specified limits should be reduced by  
1/exposureDuration in hours.  This routine implements that adjustment for its returned  
limit value.  It does not implement a further reduction of of the limit (by a factor of 2)  
for microscopes and endoilluminators.  
  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
IMPORTANT: Before using the ISO2007MPE routines, please see the notes on usage  
and responsibility in [PsychISO2007MPE](PsychISO2007MPE)/Contents.m (type "help [PsychISO2007MPE](PsychISO2007MPE)"  
at the Matlab prompt.  
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*  
  
6/25/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousCornealUVWeightedValue.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousCornealUVWeightedValue.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousCornealUVWeightedValue.m</code>
</div>

