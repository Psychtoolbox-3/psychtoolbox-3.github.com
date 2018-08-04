# [FlushEvents](FlushEvents)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[FlushEvents](FlushEvents)(['mouseUp'],['mouseDown'],['keyDown'],['autoKey'],['update'],...)  
  
Remove events from the system event queue.  
  
Removes all events of the specified types from the event queue.  
The arguments can be in any order. Empty strings are ignored.  
  
Please read the 'help ListenChar' carefully to understand various  
limitations and caveats of this function, and to learn about - often  
better - alternatives.  
  
[FlushEvents](FlushEvents) will accept all arguments for backward compatibility with  
Psychtoolbox-2, but only 'keyDown' (or no argument at all) removes  
keypress events. Events other than keypress events are not supported.  
  
See also: [GetChar](GetChar), [CharAvail](CharAvail), [FlushEvents](FlushEvents), [EventAvail](EventAvail).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/FlushEvents.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/FlushEvents.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/FlushEvents.m</code>
</div>

