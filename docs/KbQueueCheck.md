# [KbQueueCheck](KbQueueCheck)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

 [pressed, firstPress, firstRelease, lastPress, lastRelease] = [KbQueueCheck](KbQueueCheck)([deviceIndex])  
  
 Obtains data about keypresses on the specified device since the   
 most recent call to this routine, [KbQueueStart](KbQueueStart), or [KbQueueWait](KbQueueWait)  
 Clears all scored events, but unscored events that are still being  
 processsed may remain in the queue  
  
 pressed: a boolean indicating whether a key has been pressed  
  
 firstPress: an array indicating the time that each key was first  
 pressed since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
 firstRelease: an array indicating the time that each key was first  
 released since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
 lastPress: an array indicating the most recent time that each key was  
 pressed since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
 lastRelease: an array indicating the most recent time that each key  
 was released since the most recent call to [KbQueueCheck](KbQueueCheck) or   
 [KbQueueStart](KbQueueStart)  
  
 For firstPress, firstRelease, lastPress and lastRelease, a time value  
 of zero indicates that no event for the corresponding key was  
 detected since the most recent call to [KbQueueCheck](KbQueueCheck) or [KbQueueStart](KbQueueStart)  
  
 To identify specific keys, use [KbName](KbName) (e.g., [KbName](KbName)(firstPress)) to  
 generate a list of the keys for which the events occurred  
  
 For compatibility with [KbCheck](KbCheck), any key codes stored in  
 ptb\_kbcheck\_disabledKeys (see "help [DisableKeysForKbCheck](DisableKeysForKbCheck)"), will  
 not caused pressed to return as true and will be zeroed out in the  
 returned arrays. However, a better alternative is to specify a  
 keyList arguement to [KbQueueCreate](KbQueueCreate).   
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
           [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbQueueCheck.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbQueueCheck.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbQueueCheck.m</code>
</div>

