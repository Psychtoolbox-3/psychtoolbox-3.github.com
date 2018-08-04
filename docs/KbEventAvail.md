# [KbEventAvail](KbEventAvail)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

navail = [KbEventAvail](KbEventAvail)([deviceIndex])  
  
Return current number of recorded events in the event buffer of a  
keyboard queue in the return argument 'navail'.  
  
By default, the event buffer of the default keyboard queue is checked,  
but you can specify 'deviceIndex' to check the buffer of the queue  
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
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbEventAvail.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbEventAvail.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbEventAvail.m</code>
</div>

