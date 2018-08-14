# [KbPressWait](KbPressWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[secs, keyCode, deltaSecs] = [KbPressWait](KbPressWait)([deviceNumber][, untilTime=inf][, more optional args for [KbWait](KbWait)]);  
  
[KbPressWait](KbPressWait) waits for a single key press of your subject, ie. it waits  
until all keys on the keyboard are released, after that it waits for a  
a press of a key, then it returns the keyboard state and timestamp of the key  
press \*without\* waiting for the key press to finish ie, without waiting for  
a key release.  
  
It also returns if the optional deadline 'untilTime' is reached.  
  
This is a convenience wrapper, doing the same thing as  
[KbWait](KbWait)(deviceNumber, 2, ...); so read "help [KbWait](KbWait)" for details about  
operation and returned values.  
  
You'll typically use this function to ask your subject for a response and  
you want to continue your script immediately without delay, even if the  
subject keeps the key pressed for a while -- a typical usage would be if  
you want to change the stimulus immediately after response, eg, blank the  
display etc.  
  
See also: [KbPressWait](KbPressWait), [KbReleaseWait](KbReleaseWait), [KbWait](KbWait), [KbCheck](KbCheck), [KbStrokeWait](KbStrokeWait).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbPressWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbPressWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbPressWait.m</code>
</div>

