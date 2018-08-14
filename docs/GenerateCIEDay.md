# [GenerateCIEDay](GenerateCIEDay)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[spd,xd,yd] = [GenerateCIEDay](GenerateCIEDay)(Temp,[B])  
  
Generate CIE daylights of the desired correlated color  
temperature.  Formulae are from W+S, pp. 145-146.  
  
The required basis vectors may be obtained by loading  
the file B\_cieday.  
  
### INPUT  
  Temp - row vector of color temperatures.  These should be  
      in the range 4000 - 25000.  
  B - CIE daylight basis vectors.  
  
### OUTPUT  
  spd - desired spectral power distributions  
  xd  - row vector of x chromaticities  
  yd  - row vector of y chromaticities  
  
9/28/93   dhb, jms  Changed argument name to Temp  
                    If B not passed, return spd = [] and other data  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/GenerateCIEDay.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/GenerateCIEDay.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/GenerateCIEDay.m</code>
</div>

