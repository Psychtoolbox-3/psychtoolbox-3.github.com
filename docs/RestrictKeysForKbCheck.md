# [RestrictKeysForKbCheck](RestrictKeysForKbCheck)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

Restrict operation of [KbCheck](KbCheck) et al. to a subset of keys on the keyboard.  
  
oldenablekeys = [RestrictKeysForKbCheck](RestrictKeysForKbCheck)([enablekeys])  
  
Specify a vector of keycodes for keys which should be  
checked/used by [KbCheck](KbCheck) and [KbWait](KbWait). This is useful to  
only enable specific keys, e.g., to save time. The function  
returns the old set of enabled keys.  
  
Example: To enable the keys with keycodes 4, 6 and 7, do  
[RestrictKeysForKbCheck](RestrictKeysForKbCheck)([4, 6, 7]);  
  
Calling [RestrictKeysForKbCheck](RestrictKeysForKbCheck)([]); ie., with an empty vector, will  
re-enable all keys.  
  
Caution: This setting is reset to "empty" during a "clear all" command,  
ie., all keys will be enabled again after a "clear all"!  
  
### Background info:  
  
Some users of Laptops experienced the problem of "stuck keys": Some keys  
are always reported as "down", so [KbWait](KbWait) returns immediately and [KbCheck](KbCheck)  
always reports keyIsDown == 1. This is often due to special function keys.  
These keys or system functionality are assigned vendor specific  
key codes, e.g., the status of the Laptop lid (opened/closed) could be  
reported by some special keycode. Whenever the Laptop lid is open, this key  
will be reported as pressed. You can work around this problem by passing  
a subset of keycodes to be used by [KbCheck](KbCheck) and [KbWait](KbWait), whereas all other  
unwanted keys are ignored.  
  
Another advantage is a significant speed gain for [KbCheck](KbCheck) et al. on  
[MacOS](MacOS)/X systems, where the execution time of [KbChecks](KbChecks) is proportional to  
the number of keys to check.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [FlushEvents](FlushEvents), [KbName](KbName), [KbDemo](KbDemo), [KbWait](KbWait), [KbCheck](KbCheck), [GetChar](GetChar), [CharAvail](CharAvail).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/RestrictKeysForKbCheck.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/RestrictKeysForKbCheck.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/RestrictKeysForKbCheck.m</code>
</div>

