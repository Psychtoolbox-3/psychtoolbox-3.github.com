# [KbEventGet](KbEventGet)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

[event, nremaining] = [KbEventGet](KbEventGet)([deviceIndex][, maxWaitTimeSecs=0])  
  
Return oldest pending event, if any, in return argument 'event', and the  
remaining number of recorded events in the event buffer of a keyboard  
queue in the return argument 'nremaining'.  
  
By default, the event buffer of the default keyboard queue is checked,  
but you can specify 'deviceIndex' to check the buffer of the queue  
associated with 'deviceIndex'.  
  
[KbEventGet](KbEventGet)() will wait up to 'maxWaitTimeSecs' seconds for at least one  
event to show up before it gives up. By default, it doesn't wait but just  
gives up if there aren't any events queued at time of invocation.  
  
'event' is either empty if there aren't any events available, or it is a  
struct with information about the keyboard event. The returned event  
struct currently contains the following fields:  
  
'Keycode' = The [KbCheck](KbCheck) / [KbName](KbName) style keycode of the key or button that  
            triggered this event.  
  
'Time' = The [GetSecs](GetSecs) time of when the event was received.  
  
'Pressed' = 1 for a key press event, 0 for a key release event.  
  
'CookedKey' = Keycode translated into a [GetChar](GetChar)() style ASCII character code.  
Or zero if key does not have a corresponding character. Or -1 if mapping  
is unsupported for given event. This does not yet work correctly on OSX.  
  
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
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbEventGet.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbEventGet.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbEventGet.m</code>
</div>

