# [KbQueueFlush](KbQueueFlush)
##### >[Psychtoolbox](Psychtoolbox)>[PsychBasic](PsychBasic)

 nflushed = [KbQueueFlush](KbQueueFlush)([deviceIndex][flushType=1])  
  
 Flush [KbQueue](KbQueue) and/or [KbQueue](KbQueue) event buffer. By default, if flushType is  
 omitted, only the [KbQueues](KbQueues) events are deleted. Other 'flushTypes' affect  
 the [KbQueue](KbQueue) event buffer, but rather use the [KbEventFlush](KbEventFlush)() function to  
 do this.  
  
 If 'flushType' is 0, only the number of currently queued events will be  
 returned.  
  
 If 'flushType' is 1, only events returned by [KbQueueCheck](KbQueueCheck) will be flushed. This  
 is the default.  
  
 If 'flushType' is 2, only events returned by [KbEventGet](KbEventGet) will be flushed.  
  
 If 'flushType' is 3, events returned by both [KbQueueCheck](KbQueueCheck) and [KbEventGet](KbEventGet)  
 will be flushed.  
  
 If 'flushType' is 4, only the number of key-press events with valid, mapped ASCII  
 [CookedKey](CookedKey) field will be returned.  
  
 Removes all unprocessed events from the queue and zeros out any already  
 scored events.  
\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_  
  
See also: [KbQueueCreate](KbQueueCreate), [KbQueueStart](KbQueueStart), [KbQueueStop](KbQueueStop), [KbQueueCheck](KbQueueCheck),  
           [KbQueueWait](KbQueueWait), [KbQueueFlush](KbQueueFlush), [KbQueueRelease](KbQueueRelease)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychBasic/KbQueueFlush.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychBasic/KbQueueFlush.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychBasic/KbQueueFlush.m</code>
</div>

