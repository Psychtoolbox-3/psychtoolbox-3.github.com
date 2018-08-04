# [WavelengthSamplingTest](WavelengthSamplingTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[WavelengthSamplingTest](WavelengthSamplingTest)  
  
There are three formats used to represent wavelength  
sampling in the Psychtoolbox.    
  S-format      - a 3 by 1 row vector [start step numberSamples].  
  wls-format    - a list of evenly spaced wavelengths.  
  struct-format - a structure with fields start, step, and numberSamples.  
  
The S-format predates the availability of structures in MATLAB, but  
is used widely in extant code.  Low level conversion routines transform  
between these representations, and in particular routines [MakeItS](MakeItS),  
[MakeItWls](MakeItWls), and [MakeItStruct](MakeItStruct) take any of the three formats and return  
one.  By calling one of these before using wavelength format information,  
it is possible to write code that is compatible with all three.  
  
7/11/03  dhb  Wrote this test program.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/WavelengthSamplingTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/WavelengthSamplingTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/WavelengthSamplingTest.m</code>
</div>

