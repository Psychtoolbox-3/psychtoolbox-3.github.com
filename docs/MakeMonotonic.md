# [MakeMonotonic](MakeMonotonic)
##### >[Psychtoolbox](Psychtoolbox)>[PsychGamma](PsychGamma)

output = [MakeMonotonic](MakeMonotonic)(input)  
  
Make input monotonically increasing.  
  
See also [MakeGammaMonotonic](MakeGammaMonotonic), which is probably what you want if you are fitting  
gamma functions.  This routine left alone when [MakeGammaMonotonic](MakeGammaMonotonic) was created,  
in case it is called from programs completely unrelated to gamma fitting.  
  
3/1/99  dhb  Handle multiple columns.  
8/03/07 dhb  Old routine just enforced non-decreasing.  Fixed to make strictly increasing.  
3/07/10 dhb  Added comment about [MakeGammaMonotonic](MakeGammaMonotonic).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychGamma/MakeMonotonic.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychGamma/MakeMonotonic.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychGamma/MakeMonotonic.m</code>
</div>

