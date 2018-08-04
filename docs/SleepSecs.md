# [SleepSecs](SleepSecs)
##### >[Psychtoolbox](Psychtoolbox)>[PsychObsolete](PsychObsolete)

[SleepSecs](SleepSecs)(s)  
  
Wait for duration s seconds, up to one second.  [SleepSecs](SleepSecs) suspends the  
MATLAB process.       
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
If you set the priority level to greater than 0 using either [Priority](Priority) or  
[Rush](Rush) then use [SleepSecs](SleepSecs) instead of [WaitSecs](WaitSecs) while priority is elevated.  
Whereas [SleepSecs](SleepSecs) surrenders CPU time,  [WaitSecs](WaitSecs) consumes CPU time,  
exceeding limits set by [Priority](Priority) or [Rush](Rush) and causing the Mach kernel to  
revoke any priority setting greater than 0.  
  
If you are playing an animation, then use [Screen](Screen)('[Flip](Flip)') to both  
synchronize updating of the display to the Video [BLanking](BLanking) invterval (VBL)  
and to delay your animation loop until the next VBL; Like [SleepSecs](SleepSecs), [Flip](Flip)  
surrenders CPU time to other processes, abiding by limits set when  
negotiating with the kernel for priority levels \> 0.  
  
You should not need to continuously sleep the MATLAB process at high  
priority for periods greater than 1 second.  If you feel the need for   
continuous  delay at elevated priority for greater than the maximum one  
second duration of [SleepSecs](SleepSecs), consider instead lowering priority to 0,  
calling [WaitSecs](WaitSecs), and then reeleveting priority.  
  
[SleepSecs](SleepSecs) would be useful in a loop which called [KbCheck](KbCheck) at high priority  
while not displaying an animation.   
  
[SleepSecs](SleepSecs) uses the Posix usleep ("microsleep") function.  
  
OS 9: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[SleepSecs](SleepSecs) does not exist in OS 9.   
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[SleepSecs](SleepSecs) does not exist in Windows.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See Also: [Priority](Priority), [Rush](Rush), [SetMachPriorityMex](SetMachPriorityMex), [GetMachPriorityMex](GetMachPriorityMex), [Screen](Screen)('[Flip](Flip)')  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychObsolete/SleepSecs.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychObsolete/SleepSecs.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychObsolete/SleepSecs.m</code>
</div>

