# [FindSpectralPeaks](FindSpectralPeaks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychCal](PsychCal)

peaks = [FindSpectralPeaks](FindSpectralPeaks)(spectrum,[S],[noiseLevel])  
  
Find the local peaks in a spectrum.  
Uses the heuristic of requiring increasing  
and decreasing in neighborhood of peak to  
get rid of noise.  
  
Parameter noiseLevel (default 0) causes  
the routine to ignore peaks lower than  
noiseLevel\*maxValue where maxValue is the  
largest measurement in the spectrum.  
  
1/6/96      dhb     Wrote it.  
5/17/99   dhb   Added  noiseLevel parameter.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychCal/FindSpectralPeaks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychCal/FindSpectralPeaks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychCal/FindSpectralPeaks.m</code>
</div>

