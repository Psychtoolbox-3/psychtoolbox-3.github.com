# [Datapixx('StopPropixxTScopeSchedule')](Datapixx-StopPropixxTScopeSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StopPropixxTScopeSchedule');

Stop running a [PROPixx](PROPixx) T-Scope schedule. The actual hardware schedule will be  
terminated by the next [RegWr](RegWr)\* command.  
Note that if maxScheduleFrames was assigned a non-0 value in  
[SetPropixxTScopeSchedule](SetPropixxTScopeSchedule), then the schedule can be left to terminate  
automatically without having to call [StopPropixxTScopeSchedule](StopPropixxTScopeSchedule).  
See [Propixx10kHzTScopeDemo](Propixx10kHzTScopeDemo).m for an example.  
  


###See also:
[StartPropixxTScopeSchedule](Datapixx-StartPropixxTScopeSchedule)
