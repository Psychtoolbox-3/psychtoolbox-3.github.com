# [Datapixx('StartDacSchedule')](Datapixx-StartDacSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Start running a DAC waveform playback schedule. The actual hardware schedule  
will be initiated by the next [RegWr](RegWr)\* command, and then the first waveform sample  
will hit the [DACs](DACs) after the scheduleOnset specified in [SetDacSchedule](SetDacSchedule).  
Note that every call to [StartDacSchedule](StartDacSchedule) must be preceeded by a call to  
[SetDacSchedule](SetDacSchedule) (ie: multiple calls to [StartDacSchedule](StartDacSchedule) each require their own  
call to [SetDacSchedule)](SetDacSchedule)).  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[SetDacSchedule](Datapixx-SetDacSchedule), [StopDacSchedule](Datapixx-StopDacSchedule), [GetDacStatus](Datapixx-GetDacStatus)
