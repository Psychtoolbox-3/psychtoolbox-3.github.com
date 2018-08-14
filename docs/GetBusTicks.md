# [GetBusTicks](GetBusTicks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

ticks = [GetBusTicks](GetBusTicks)  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Return the number of system bus ticks since startup.  The period of the  
bus tick clock depends on the model and frequency of your CPU. Use  
[GetSecs](GetSecs) instead for reliable, high-precision time measurement in standard  
units.  
  
Bus ticks returned by [GetBusTicks](GetBusTicks) are not the same as ticks returned by  
[GetTicks](GetTicks).  The [GetBusTicks](GetBusTicks) clock is fast and precise, derived directly  
from the CPU clock and typically faster than 1/10 of its speed. On  
Allen's 1GHz G4 the [GetBusTicks](GetBusTicks) clock is 133 [MHz](MHz).  
  
The [GetTicks](GetTicks) clock is slow, always 1/60.15 seconds. On OS  
X [GetTicks](GetTicks) is obsolete and provided only for compatability with older  
scripts.       
  
TIMING ADVICE: the first time you access any MEX function or M file,  
Matlab takes several hundred milliseconds to load it from disk.  
Allocating a variable takes time too. Usually you'll want to omit those  
delays from your timing measurements by making sure all the functions you  
use are loaded and that all the variables you use are allocated, before  
you start timing. MEX files stay loaded until you flush the MEX files  
(e.g. by changing directory or calling CLEAR MEX). M files and variables  
stay in memory until you clear them.  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetBusTicks](GetBusTicks) does not exist in OS 9.   
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[GetBusTicks](GetBusTicks) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [GetBusTicksTick](GetBusTicksTick), [GetSecs](GetSecs), [GetSecsTick](GetSecsTick),  [GetTicks](GetTicks), [GetTicksTick](GetTicksTick).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/GetBusTicks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/GetBusTicks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/GetBusTicks.m</code>
</div>

