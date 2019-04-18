# [Datapixx('StartPropixxTScopeSchedule')](Datapixx-StartPropixxTScopeSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StartPropixxTScopeSchedule');

Start running a [PROPixx](PROPixx) T-Scope schedule. The actual hardware schedule will be  
initiated by the next [RegWr](RegWr)\* command, and then the first T-Scope image will  
replace the cover page after the scheduleOnset specified in  
[SetPropixxTScopeSchedule](SetPropixxTScopeSchedule).  
Note that every call to [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule) must be preceeded by a call  
to [SetPropixxTScopeSchedule](SetPropixxTScopeSchedule) (ie: multiple calls to [StartPropixxTScopeSchedule](StartPropixxTScopeSchedule)  
each require their own call to [SetPropixxTScopeSchedule)](SetPropixxTScopeSchedule)).  
See [Propixx10kHzTScopeDemo](Propixx10kHzTScopeDemo).m for an example.  
  


###See also:
[SetPropixxTScopeSchedule](Datapixx-SetPropixxTScopeSchedule), [StopPropixxTScopeSchedule](Datapixx-StopPropixxTScopeSchedule), [EnablePropixxTScope](Datapixx-EnablePropixxTScope), [EnablePropixxTScopePrepRequest](Datapixx-EnablePropixxTScopePrepRequest), [WritePropixxTScopePages](Datapixx-WritePropixxTScopePages)
