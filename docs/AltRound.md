# [AltRound](AltRound)
##### >[Psychtoolbox](Psychtoolbox)>[PsychSignal](PsychSignal)

out = [AltRound](AltRound)(nr,factor)  
rounds the elements in NR to the nearest multiple  
of FACTOR.  
  
FACTOR must be either a scalar or of the same shape as NR.  
  
Thus:  
  [AltRound](AltRound)(12.26,.25) = 12.25;  
  [AltRound](AltRound)(12.2 ,0.6) = 12,  
  but also  
  [AltRound](AltRound)(1449 ,100) = 1400.  
  
DN 2008  
DN 2009-02-02 Support non-scalar factor input  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychSignal/AltRound.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychSignal/AltRound.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychSignal/AltRound.m</code>
</div>

