# [uvTols](uvTols)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

ls = [uvTols](uvTols)(uv)  
  
Convert CIE u'v' chromaticity to cone chromaticity ls, L/(L+M+S), S/(L+M+S).  
  
Uses regression conversion matrix based on Judd-Vos XYZ and  
Smith-Pokorny cone fundamentals to get from XYX to LMS.  This  
is an exact linear transformation and so you don't get as many  
weird little numerical things happening when you apply this to  
uv for spectral lights.  
  
3/17/04  dhb        Wrote it.  
05/06/11 dhb      Make function name in file match actual function name.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/uvTols.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/uvTols.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/uvTols.m</code>
</div>

