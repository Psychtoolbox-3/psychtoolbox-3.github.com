# [WaitTicks](WaitTicks)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[WaitTicks](WaitTicks)(wait)  
  
Wait the requested number of system ticks. One tick is 1/60.15 seconds.  
  
TIMING ADVICE: the first time you access any MEX function or M file,  
Matlab takes several hundred milliseconds to load it from disk.  
Allocating a variable takes time too. Usually you'll want to omit  
those delays from your timing measurements by making sure all the  
functions you use are loaded and that all the variables you use are  
allocated, before you start timing. MEX files stay loaded until you  
flush the MEX files (e.g. by changing directory or calling CLEAR  
MEX). M files and variables stay in memory until you clear them.  
  
  
Windows: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[WaitTicks](WaitTicks) is implemented using [WaitSecs](WaitSecs).m, and each tick is interpreted   
as 1/60.15 seconds to be consistent with the Mac version.  
(In Windows, a system tick is usually 1 millisecond, but with a precision that  
varies from system to system. We're ignoring the system ticks here.)  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
"Ticks" functions are deprecated, use "Secs" functions instead;  To  
measure time, use [GetSecs](GetSecs) insted of [GetTicks](GetTicks). To delay, use [WaitSecs](WaitSecs)  
instead of [WaitTicks](WaitTicks).    
  
"Secs" functions are provided for OS 9, Windows, and OS X and are more precise  
and more accurate than "Ticks" functions.    
  
[WaitTicks](WaitTicks) behaves exactly as on OS 9, relying on the Psychtoolbox mex  
function [GetTicks](GetTicks) to read the system tick count.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [GetTicks](GetTicks), [GetSecs](GetSecs), [WaitSecs](WaitSecs).  
  
6/14/95 dhb  Added to help.  
1/29/97 dhb  More comments.  
3/15/97 dgp  Expanded comments.  
3/15/99 xmz  Put in conditional for Windows.  
2/12/04 awi  Added the OS X case.  Fixed the Windows case so that it  
             waits an integer number of ticks.  Simplified platform test  
             expressions.  Added test for unfamiliar platform.  Added OS X   
             section to comments.    




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/WaitTicks.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/WaitTicks.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/WaitTicks.m</code>
</div>

