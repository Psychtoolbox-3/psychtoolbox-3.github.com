# [FillPolyTest](FillPolyTest)
##### >[Psychtoolbox](Psychtoolbox)>[PsychTests](PsychTests)

[FillPolyTest](FillPolyTest)  
  
Test [Screen](Screen) 'FillPoly' for speed and correctness.  
  
[Screen](Screen) 'FillPoly' renders both convex and concave polygons, but treats  
them differently; Convex polygons it renders quickly using GL\_POLYGON.  
Concave polygons it renders slowly using GLU tesselators.    
  
[FillPolyTest](FillPolyTest) draws a "Butterfly" concave polygon to test if [FillPolly](FillPolly)  
correctly detects and renders concave polygons.  If [FillPoly](FillPoly) failed to   
detect concavity, it would use GL\_POLYGON, which renders concave polygons  
incorrectly.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychTests/FillPolyTest.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychTests/FillPolyTest.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychTests/FillPolyTest.m</code>
</div>

