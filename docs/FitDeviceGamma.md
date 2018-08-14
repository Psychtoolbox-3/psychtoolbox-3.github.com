# [FitDeviceGamma](FitDeviceGamma)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

function [gammaFit,gammaInputFit,fitComment,gammaParams] = ...  
  [FitDeviceGamma](FitDeviceGamma)(gammaRaw,gammaInputRaw,[fitType],[nInputLevels])  
  
Fit the measured gamma function.  Appends 0 measurement,  
arranges data for fit, etc.  
  
The returned gamma functions are normalized to a maximum of 1.  
  
If present, argument fitType is passed on to [FitGamma](FitGamma).  
  
11/14/06  dhb  Convert for [0-1] universe.  Add nInputLevels arg.  
5/27/10   dhb  Allow gammaInputRaw to be either a single column or a matrix with same number of columns as devices.  
               Check that last input values are unity.  
4/12/11   dhb  Return the parameter vector of whatever functional form was fit  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/FitDeviceGamma.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/FitDeviceGamma.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/FitDeviceGamma.m</code>
</div>

