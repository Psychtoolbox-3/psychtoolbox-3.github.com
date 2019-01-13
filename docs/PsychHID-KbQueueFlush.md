# [PsychHID('KbQueueFlush')](PsychHID-KbQueueFlush) 
##### [Psychtoolbox](Psychtoolbox)>[PsychHID](PsychHID).{mex*} subfunction


Flushes all scored and unscored keyboard events from a queue.  
Returns number of events 'navail' in keyboard event buffer before the flush  
takes place.  
If 'flushType' is 0, only the number of currently queued events will be  
returned.  
If 'flushType' is 1, only events returned by [KbQueueCheck](KbQueueCheck) will be flushed. This  
is the default.  
If 'flushType' is 2, only events returned by [KbQueueGetEvent](KbQueueGetEvent) will be flushed.  
If 'flushType' is 3, events returned by both [KbQueueCheck](KbQueueCheck) and [KbQueueGetEvent](KbQueueGetEvent)  
will be flushed.  
If 'flushType' & 4, only the number of key-press events with valid, mapped ASCII  
[CookedKey](CookedKey) field will be returned.  
[PsychHID](PsychHID)('KbQueueCreate') must be called before this routine.  
The optional 'deviceIndex' is the index of the HID input device whose queue  
should be flushed. If omitted, the queue of the default device will be flushed.  
  


###See also:
[KbQueueCreate](PsychHID-KbQueueCreate), [KbQueueStart](PsychHID-KbQueueStart), [KbQueueStop](PsychHID-KbQueueStop), [KbQueueCheck](PsychHID-KbQueueCheck), [KbQueueRelease](PsychHID-KbQueueRelease)
