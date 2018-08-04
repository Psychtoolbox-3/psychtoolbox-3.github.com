# [Datapixx('RegWrVideoSync')](Datapixx-RegWrVideoSync) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Write local register cache modifications to Datapixx at leading edge of next  
video vertical sync pulse. This is a good way to write Datapixx registers with  
microsecond synchronization to the start of a video frame. All Datapixx Set\*  
functions do fast writes to a local register cache on the host, and all Datapixx  
Get\* functions do fast reads from this local register cache. [RegWrVideoSync](RegWrVideoSync)  
writes these cached register modifications back to the Datapixx over USB. The  
cache writeback USB message is sent immediately and this function returns  
quickly, but the Datapixx itself waits until the next vertical sync pulse before  
writing the registers.  
This call could be followed by a [Screen](Screen)('[Flip](Flip)', win) command to synchronize  
register writes to presentation of a new video image.  
Note that if the [Screen](Screen)('[Flip](Flip)', win, when) form is used, the new video image may  
be delayed many frames after the register cache is written.  
See [DatapixxDacSyncDemo](DatapixxDacSyncDemo).m and [DatapixxAdcAcquireDemo](DatapixxAdcAcquireDemo).m for examples.  
  


###See also:
[RegWr](Datapixx-RegWr), [RegWrRdVideoSync](Datapixx-RegWrRdVideoSync), [RegWrPixelSync](Datapixx-RegWrPixelSync)
