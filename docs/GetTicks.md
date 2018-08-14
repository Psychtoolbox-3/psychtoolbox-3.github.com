# [GetTicks](GetTicks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

ticks = [GetTicks](GetTicks)  
  
The number of system ticks since startup. One tick is 1/60.15 second.  
  
For more precise timing use [GetSecs](GetSecs) or [WaitSecs](WaitSecs).  
  
TIMING ADVICE: the first time you access any MEX function or M file,  
Matlab takes several hundred milliseconds to load it from disk.  
Allocating a variable takes time too. Usually you'll want to omit  
those delays from your timing measurements by making sure all the  
functions you use are loaded and that all the variables you use are  
allocated, before you start timing. MEX files stay loaded until you  
flush the MEX files (e.g. by changing directory or calling CLEAR  
MEX). M files and variables stay in memory until you clear them.  
  
See also: [WaitTicks](WaitTicks), [GetTicksTick](GetTicksTick), [GetSecs](GetSecs), [GetSecsTick](GetSecsTick), [WaitSecs](WaitSecs), [GetChar](GetChar), [GetBusTicks](GetBusTicks), [GetBusTicksTick](GetBusTicksTick).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/GetTicks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/GetTicks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/GetTicks.m</code>
</div>

