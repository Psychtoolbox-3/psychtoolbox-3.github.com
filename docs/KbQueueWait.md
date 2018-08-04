# [KbQueueWait](KbQueueWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

secs=[KbQueueWait](KbQueueWait)([deviceIndex][, forWhat=0][, untilTime=inf])  
  
Waits for any key to be pressed and returns the time of the press. The  
optional 'forWhat' parameter controls what kind of event is waited for  
(similar to [KbWait)](KbWait)).  
forWhat:  
0: return as soon as a key is down  
1: return as soon as no keys are down  
2: wait for a key press (so if a key is already down upon function  
   entering, it is ignored):  
   waitForAllKeysReleased -\> waitForKeypress  
3: wait for a keystroke like, 2, but wait until key is released after  
   pressing it:  
   waitForAllKeysReleased -\> waitForKeypress -\> waitForAllKeysReleased  
  
If the optional parameter 'untilTime' is provided, [KbWait](KbWait) will only wait  
until that time and then return regardless if anything happened on the  
keyboard or not.  
  
[KbQueueFlush](KbQueueFlush) should not be called immediately prior to this function. If  
you do that and clear prior events, [KbQueueWait](KbQueueWait) is not able to determine  
whether a key is down or not upon function entry (important for all four  
forWhat modes). It will assume no keys are down and, e.g., return  
immediate when forWhat is 1 even though a key was depressed before the  
flush and is still being held. [KbQueueWait](KbQueueWait) correctly deals with previous  
events in the buffer.  
NB. Previously, use of [KbQueueFlush](KbQueueFlush) before calling this function was  
recommended. The current function maintains backwards compatibility for  
this use case. However, any changes of existing code to follow the new  
recommendation and remove preceding [KbQueueFlush](KbQueueFlush) calls should be  
carefully considered and tested (don't change what works).  
  
Note that this command will not respond to any keys that were inactivated  
by using the keyList argument to [KbQueueCreate](KbQueueCreate).  
  
Since [KbQueueWait](KbQueueWait) is implemented as a looping call to [KbQueueCheck](KbQueueCheck), it  
will not respond to any key codes stored in the global variable  
ptb\_kbcheck\_disabledKeys (see "help [DisableKeysForKbCheck](DisableKeysForKbCheck)")  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
           [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbQueueWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbQueueWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbQueueWait.m</code>
</div>

