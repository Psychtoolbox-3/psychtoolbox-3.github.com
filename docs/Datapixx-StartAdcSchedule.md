# [Datapixx('StartAdcSchedule')](Datapixx-StartAdcSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StartAdcSchedule');

Start running an ADC analog acquisition schedule. The actual hardware schedule  
will be initiated by the next [RegWr](RegWr)\* command, and then the [ADCs](ADCs) will acquire  
their first sample after the scheduleOnset specified in [SetAdcSchedule](SetAdcSchedule).  
Note that every call to [StartAdcSchedule](StartAdcSchedule) must be preceeded by a call to  
[SetAdcSchedule](SetAdcSchedule) (ie: multiple calls to [StartAdcSchedule](StartAdcSchedule) each require their own  
call to [SetAdcSchedule)](SetAdcSchedule)).  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[SetAdcSchedule](Datapixx-SetAdcSchedule), [StopAdcSchedule](Datapixx-StopAdcSchedule), [GetAdcStatus](Datapixx-GetAdcStatus), [ReadAdcBuffer](Datapixx-ReadAdcBuffer)
