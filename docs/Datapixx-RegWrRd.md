# [Datapixx('RegWrRd')](Datapixx-RegWrRd) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('RegWrRd');

Write local register cache modifications to Datapixx immediately, then read back  
Datapixx register snapshot to local cache. All Datapixx Set\* functions do fast  
writes to a local register cache on the host, and all Datapixx Get\* functions do  
fast reads from this local register cache. [RegWrRd](RegWrRd) writes these cached register  
modifications back to the Datapixx over USB, then uploads over USB a fresh  
snapshot of the Datapixx registers into the local cache.  
  


###See also:
[RegWr](Datapixx-RegWr), [RegWrRdVideoSync](Datapixx-RegWrRdVideoSync), [RegWrRdPixelSync](Datapixx-RegWrRdPixelSync)
