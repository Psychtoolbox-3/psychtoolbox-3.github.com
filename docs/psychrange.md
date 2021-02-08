# [psychrange](psychrange)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

r = psychrange(X [, dims]) - Drop in replacement for range().  
  
See Matlab online docs, or Octave help for range().  
  
Matlab does not have range() outside the statistics toolbox, and we do  
not want to enforce installation of it for the few use-cases we have  
internally for range(), so provide this drop-in / fallback inplementation.  
  
Octave would not benefit from this, as range is part of statistics package,  
but so are min and max, so if range isn't there, the min and max functions  
needed here won't be either.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/psychrange.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/psychrange.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/psychrange.m</code>
</div>

