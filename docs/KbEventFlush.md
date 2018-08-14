# [KbEventFlush](KbEventFlush)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

nflushed = [KbEventFlush](KbEventFlush)([deviceIndex])  
  
Flush event buffer of a keyboard queue. This removes all stored events  
from the keyboard event buffer of a given keyboard queue. It returns the  
number of removed events in the optional return argument 'nflushed'.  
  
By default, the event buffer of the default keyboard queue is emptied,  
but you can specify 'deviceIndex' to flush the buffer of the queue  
associated with 'deviceIndex'.  
  
Keyboard event buffers are a different way to access the information  
collected by keyboard queues. Before you can use an event buffer you  
always must create its "parent keyboard queue" via [KbQueueCreate](KbQueueCreate)() and  
call [KbQueueStart](KbQueueStart)() to enable key event recording. See "help  
[KbQueueCreate](KbQueueCreate)" etc. on how to do this.  
  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
           [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbEventFlush.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbEventFlush.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbEventFlush.m</code>
</div>

