# [Priority](Priority)
##### >[Psychtoolbox](Psychtoolbox)>[PsychPriority](PsychPriority)

oldPriority=[Priority](Priority)([newPriority])  
  
Query and optionally set the execution priority of your script to  
'newPriority' and switch from non-realtime to realtime scheduling (for  
'newPriority' values greater than zero).  
  
Higher priority levels will reduce the chance of other running  
applications and system processes interfering with the execution timing  
of your script, or reduce the severity of interference. However, various  
factors influence the timing behaviour of your computer and its hardware,  
so while use of [Priority](Priority)() is one step to ensure good timing, it is not  
the only required step. The [PsychDocumentation](PsychDocumentation) subfolder of your  
distribution as well as the Psychtoolbox Wiki contain various documents  
with tips on how to improve system timing behaviour. All else being  
equal, the Linux operating system should provide best possible timing  
behaviour out of the box, with various possibilities to tweak and tune the  
system for even better timing behaviour. Mac OSX is the second best  
choice for precise timing.  
  
OS X: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
Unlike on OS 9 and Windows, On OS X setting a high priority will not  
disable important parts of your computer such as the keybaord and hard  
drive. [Priority](Priority) calls the Psychtoolbox mex function [MachSetPriority](MachSetPriority).  For  
simple, OS-neutral control of process priority on OS X use [Priority](Priority). For  
complicated, fine-grained, OS-specific control of process priority use  
[MachSetPriority](MachSetPriority).      
  
At priority settings greater than 0, your script must limit MATLAB's  use  
of CPU time to stay within the limits specified by the priority value.  
The consequence of failing to restrict the CPU time to the limits  
specified by the priority values is that OS X will demote MATLAB back to  
priority 0. You can check to see if this has happened by calling  
[Priority](Priority) with no arguments.  
  
### Within a script there are two ways to limit MATLAB's use of CPU time:  
  
  1. Call "[WaitSecs](WaitSecs)"   
  2. Call [Screen](Screen)('[Flip](Flip)',...)  
  
Both calls will sleep the main MATLAB thread, surrendering CPU time to  
other threads on the system until the MATLAB thread is awakened.  
[WaitSecs](WaitSecs) sleeps the MATLAB thread for a specified period.  
[Screen](Screen)('[Flip](Flip)',...) sleeps the MATLAB thread until the next video blanking  
interval.  
  
The priority value corresponds to the proportion of the video frame  
period  during which MATLAB is guranteed 100 percent of CPU time:  
  
  [GuaranteedCPUtimePerFramePeriod](GuaranteedCPUtimePerFramePeriod) = priority/10 \* framePeriod  
  
If your computer has multiple video displays running at different frame  
rates then [Priority](Priority) will choose the shortest frame period.  
  
The consequence of a thread exceeding the specified limits on CPU usage  
are that the MACH kernel will revoke its real-time priority status.  
However, the threshold at which the MACH kernel decices to revoke  
priority is not known.  We have observed that at 100% CPU usage the  
Jaguar Mach kernel will revoke priority after 2.5 seconds, indepent of  
the CPU time requested when setting priority.    
  
Note that if you change the video frame rate after setting priority then  
the framePeriod which [Priority](Priority) used when setting the priority level will  
no longer match the true frame period. Therefore you should change the  
priority level after changing the video mode and not before.   
  
  
WINDOWS: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
For the Windows version of [Priority](Priority) (and [Rush](Rush)), the priority levels set  
are  "process priority levels". There are 3 priority levels available,  
levels 0, 1, and 2. Level 0 is "normal priority level", level 1 is "high  
priority level", and level 2 is "real time priority level". Combined with  
thread priority levels, they determine the absolute priority level of the  
Psychtoolbox threads. Threads are executed in a "round robin" fashion on  
Windows, with the  lower priority threads getting cpu time slice only  
when no higher priority thread is ready to execute. Currently, no tests  
have been done to see what tasks are pre-empted by setting the Matlab  
process to real-time priority. It does seem to block keyboard input,  
though, so for example if you have a clut animation going on at priority  
level 2, then the force-quit key combo (Ctrl-Alt-Delete) does not  work.  
However, the keyboard inputs are still sent to the message queue, so  
[GetChar](GetChar) or [GetClicks](GetClicks) still work if they are also called at priority level  
2.  
  
Typically you will not want to choose a higher priority than 1 unless you  
know exactly what you're doing.  
  
LINUX: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
To enable use of [Priority](Priority)(), you must run the script  
[PsychLinuxConfiguration](PsychLinuxConfiguration) at least once and follow its instructions.  
Normally the script will get executed automatically by our installer if  
you got Psychtoolbox via [DownloadPsychtoolbox](DownloadPsychtoolbox) or [UpdatePsychtoolbox](UpdatePsychtoolbox).  
However, if you got Psychtoolbox directly from the package manager of  
your Linux distribution or from the [NeuroDebian](NeuroDebian) repositories, it may be  
neccessary to execute the [PsychLinuxConfiguration](PsychLinuxConfiguration) function manually.  
  
GNU/Linux supports priority levels between 0 and 99. Zero means standard  
non-realtime timesharing operation -- Play fair with all other  
applications. Increasing values greater than zero mean realtime mode: The  
Matlab/Octave process is scheduled in realtime mode with a priority  
corresponding to the given number - higher means better, but also more  
likelihood of interfering with system processes. Try to stick to a level  
of 1 unless you have reason to go higher. Level one is usually  
sufficient, unless you run other realtime applications on the same  
machine in parallel and want to prioritize Psychtoolbox relative to those  
applications.  
  
In realtime mode, PTB will also try to lock down all of Matlab/Octaves  
memory into physical RAM, preventing it from being paged out to disk by  
the virtual memory manager. If it works, it's great! However, the amount  
of lockable memory is restricted to max. 50% of installed RAM memory on  
some older Linux setups, so if Matlab/Octave/your experiment would need  
more than 50% of available system memory, this will fail. PTB will output  
an informative warning in this case, but continue otherwise unaffected.  
Realtime scheduling will be still effective, you'll just lose the bonus  
of memory locking.  
  
On old single processor computers, be careful not to create any  
uninterruptible infinite loops in your code when running realtime,  
otherwise your system may lock up, requiring a hard reboot!  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
see also OS X:    [Rush](Rush)  
see also Windows: [Rush](Rush)  
see also OS 9:    [Rush](Rush), [ScreenTest](ScreenTest), [RushTest](RushTest), [LoopTest](LoopTest)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychPriority/Priority.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychPriority/Priority.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychPriority/Priority.m</code>
</div>

