# [ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue](ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRadiometric](PsychRadiometric)>[PsychISO2007MPE](PsychISO2007MPE)

[val\_UWattsPerCm2,limit\_UWattsPerCm2] = [ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue](ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue)(S,irradiance\_uWattsPerCm2,stimulusDurationSecs)  
  
Compute the unweighted radiation for anterior segment convergent beam value, for Type 1 instruments as given on page 8, Table 2,   
5.4.1.5.  This limit applies only to convergent beams, whatever they are.  I'm guessing this is what a Maxwellian view produces,  
however, as in that case the beam is brought to a waist inside the eye.  In this case, the limit applies to the irradiance  
at the beam waist over the 1 mm diameter aperture with the highest irradiance.  
  
Unlike all the other routines in this suite, the key quantity is probably not best passed as stimulus radiance.  Rather, for  
this type of optical system, the relevant irradiance should be measured directly.  
  
NOTE: This routine has not been tested, since I (DHB) don't have any instrument currently that produces the relevant type of  
stimulus.  I added it as a placeholder for convenience.  There is an error statement to keep it from being used  
until it is tested.  
  
Input spectrum is radiance in units of [UWatts](UWatts)/[m2-wlinterval].  
  
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
  
6/28/13  dhb  Wrote it.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRadiometric/PsychISO2007MPE/ISO2007MPEComputeType1ContinuousAntConvrgUnweightedValue.m</code>
</div>

