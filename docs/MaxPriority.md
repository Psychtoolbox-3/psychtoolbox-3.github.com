# [MaxPriority](MaxPriority)
##### >[Psychtoolbox](Psychtoolbox)>[PsychPriority](PsychPriority)

priorityLevel=[MaxPriority](MaxPriority)([windowPtrOrScreenNumber],['WaitBlanking'],['PeekBlanking'],...  
                            ['BlankingInterrupt'],['SetClut'],['ClutMovie'],...  
                            ['SND'],['sound'],['speak'],...  
                            ['GetSecs'],['WaitSecs'],['cputime'],...  
                            ['KbCheck'],['KbWait'],['CharAvail'],['GetChar'],...  
                            ['EventAvail'],['GetClicks'],['GetMouse'],['GetTicks'])  
  
[MaxPriority](MaxPriority).m receives a list of one or more function names, in any  
order, and returns the maximum priorityLevel that will allow all the  
named functions to work normally on this computer. Use [MaxPriority](MaxPriority)  
before calling RUSH, to select the highest priorityLevel that's  
compatible with all the functions that you're rushing.  
  
The name matching ignores case.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
On OS X all priority levels are safe for all functions. [MaxPriority](MaxPriority)  
always returns 9, the highest priority level.  
  
To preserve compatibility with other platforms we recommend using  
[MaxPriority](MaxPriority) in your script on OS X, instead of the constant 9.  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[Priority](Priority) levels returned by [MaxPriority](MaxPriority) are 0, 1 and 2.  
Although use of priority levels \> 1 is possible and allowed by [MaxPriority](MaxPriority)  
if you don't try to acquire input from keyboard or mouse, it is discouraged  
to use levels \> 1 as this can interfere with execution of a lot of  
important system processes and severely reduce the stability of  
Windows execution.  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
[MaxPriority](MaxPriority) always returns 1, although levels of up to 99 are possible.  
We recommend to sticking to the lowest level, unless some tweaking for a  
specific setup or situation is necessary.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See RUSH, [Priority](Priority), [MovieDemo](MovieDemo), [ScreenTest](ScreenTest), SCREEN [Preference](Preference) [MaxPriorityForBlankingInterrupt](MaxPriorityForBlankingInterrupt),  
SCREEN [Preference](Preference) [SetClutPunchesBlankingClock](SetClutPunchesBlankingClock).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychPriority/MaxPriority.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychPriority/MaxPriority.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychPriority/MaxPriority.m</code>
</div>

