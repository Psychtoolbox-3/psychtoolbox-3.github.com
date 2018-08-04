# [KbQueueDemo](KbQueueDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

% [KbQueueDemo](KbQueueDemo)([deviceIndex])  
 Shows how to detect when the user has pressed a key.  
 See [KbQueueCheck](KbQueueCheck), [KbQueueWait](KbQueueWait), [KbName](KbName), [KbCheck](KbCheck), [KbWait](KbWait), [GetChar](GetChar), [CharAvail](CharAvail).  
  
 The [KbQueueXXX](KbQueueXXX) functions are low-level like [KbCheck](KbCheck) and [KbWait](KbWait), but, like  
 [GetChar](GetChar)/[CharAvail](CharAvail), they use a queue so that brief events can be captured.  
  
 Like [GetChar](GetChar)/[CharAvail](CharAvail), [KbQueueXXX](KbQueueXXX) functions may be used  
 asychronously - the OS will pick up the character whether your code  
 is currently looking for it or not so long as the queue has already been   
 created(using [KbQueueCreate)](KbQueueCreate)) and started (using [KbQueueStart)](KbQueueStart)).  
  
 Unlike [GetChar](GetChar)/[CharAvail](CharAvail), [KbQueueXXX](KbQueueXXX) functions can detect isolated presses  
 of modifier keys. Also, the times of key presses should be more accurate than  
 those associated with [GetChar](GetChar)/[CharAvail](CharAvail) or with [KbCheck](KbCheck) and the timebase is  
 the same as that returned by [GetSecs](GetSecs) (unlike [GetChar](GetChar)/[CharAvail)](CharAvail)).  
  
 The first four demos here are analogous to those in [KbDemo](KbDemo).m  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/KbQueueDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/KbQueueDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/KbQueueDemo.m</code>
</div>

