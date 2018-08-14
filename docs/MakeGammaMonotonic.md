# [MakeGammaMonotonic](MakeGammaMonotonic)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

output = [MakeGammaMonotonic](MakeGammaMonotonic)(input)  
  
Make input monotonically increasing from lowest value.  
  
This version also forces the last value to be 1, and then  
enforces decreasing downwards from there, after the  
enforcement of increasing from 0.  
  
3/1/99  dhb  Handle multiple columns.  
8/03/07 dhb  Old routine just enforced non-decreasing.  Fixed to make strictly increasing.  
3/07/10 dhb  Wrote from [MakeMonotonic](MakeMonotonic).  
             Did not want to change behavior of [MakeMonotonic](MakeMonotonic) in case it is called from  
             programs unrelated to gamma fitting.  
3/08/10 dhb  Actually do the enforcement of 1.  
5/27/10 dhb  Use a larger bump, 100\*eps  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/MakeGammaMonotonic.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/MakeGammaMonotonic.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/MakeGammaMonotonic.m</code>
</div>

