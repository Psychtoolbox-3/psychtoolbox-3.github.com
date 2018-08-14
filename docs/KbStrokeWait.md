# [KbStrokeWait](KbStrokeWait)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[secs, keyCode, deltaSecs] = [KbStrokeWait](KbStrokeWait)([deviceNumber][, untilTime=inf][, more optional args for [KbWait](KbWait)]);  
  
[KbStrokeWait](KbStrokeWait) waits for a single keystroke of your subject, ie. it waits  
until all keys on the keyboard are released, after that it waits for a  
single keystroke - a single press of a key, followed by releasing the key  
again. After the subject has finished its "keystroke" and released the key,  
[KbStrokeWait](KbStrokeWait) returns the keyboard state and timestamp of the key press.  
  
It also returns if the optional deadline 'untilTime' is reached.  
  
This is a convenience wrapper, doing the same thing as  
[KbWait](KbWait)(deviceNumber, 3, ...); so read "help [KbWait](KbWait)" for details about  
operation and returned values.  
  
You'll typically use this function to ask your subject for input of a  
single character, or for confirmation of something (e.g., "Press any key  
when you're ready for the next block of trials").  
  
See also: [KbPressWait](KbPressWait), [KbReleaseWait](KbReleaseWait), [KbWait](KbWait), [KbCheck](KbCheck), [KbStrokeWait](KbStrokeWait).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbStrokeWait.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbStrokeWait.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbStrokeWait.m</code>
</div>

