# [CharAvail](CharAvail)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[avail, numChars] = [CharAvail](CharAvail)  
  
[CharAvail](CharAvail) returns the availability of characters in the keyboard event  
queue and sometimes the queue's current size. "avail" will be 1 if  
characters are available, 0 otherwise.  "numChars" may hold the current  
number of characters in the event queue, but in some system  
configurations it is just empty, so do not rely on numChars providing  
meaningful results, unless you've tested it on your specific setup.  
  
Please read the 'help ListenChar' carefully to understand various  
limitations and caveats of this function, and to learn about - often  
better - alternatives.  
  
Note that this routine does not actually remove characters from the event  
queue. Call [GetChar](GetChar) to remove characters from the queue.  
  
[GetChar](GetChar) and [CharAvail](CharAvail) are character-oriented (and slow), whereas [KbCheck](KbCheck)  
and [KbWait](KbWait) are keypress-oriented (and fast). See [KbCheck](KbCheck).  
  
See also: [GetChar](GetChar), [ListenChar](ListenChar), [FlushEvents](FlushEvents), [KbCheck](KbCheck), [KbWait](KbWait), [KbDemo](KbDemo),  
[KbQueueDemo](KbQueueDemo).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/CharAvail.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/CharAvail.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/CharAvail.m</code>
</div>

