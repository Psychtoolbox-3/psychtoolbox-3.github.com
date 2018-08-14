# [Datapixx('RegWrRdVideoSync')](Datapixx-RegWrRdVideoSync) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Write local register cache modifications to Datapixx at leading edge of next  
video vertical sync pulse, then read back Datapixx register snapshot to local  
cache. This is a good way to write Datapixx registers with microsecond  
synchronization to the start of a video frame, then pause program execution  
until after onset of the vertical sync pulse. All Datapixx Set\* functions do  
fast writes to a local register cache on the host, and all Datapixx Get\*  
functions do fast reads from this local register cache. [RegWrRdVideoSync](RegWrRdVideoSync) writes  
these cached register modifications back to the Datapixx over USB, then waits  
for a fresh snapshot of the Datapixx registers to be returned over USB. The  
cache writeback USB message is sent immediately, but the Datapixx itself waits  
until the next vertical sync pulse before writing the registers.  
[RegWrRdVideoSync](RegWrRdVideoSync) returns when registers are read back after the vertical sync  
onset.  
  


###See also:
[RegWrRd](Datapixx-RegWrRd), [RegWrVideoSync](Datapixx-RegWrVideoSync), [RegWrRdPixelSync](Datapixx-RegWrRdPixelSync)
