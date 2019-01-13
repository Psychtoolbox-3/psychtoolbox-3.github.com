# [Datapixx('StartDoutSchedule')](Datapixx-StartDoutSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StartDoutSchedule');

Start running a digital output waveform playback schedule. The actual hardware  
schedule will be initiated by the next [RegWr](RegWr)\* command, and then the first  
waveform sample will hit the digital outputs after the scheduleOnset specified  
in [SetDoutSchedule](SetDoutSchedule).  
Note that every call to [StartDoutSchedule](StartDoutSchedule) must be preceeded by a call to  
[SetDoutSchedule](SetDoutSchedule) (ie: multiple calls to [StartDoutSchedule](StartDoutSchedule) each require their own  
call to [SetDoutSchedule)](SetDoutSchedule)).  
See [DatapixxDout](DatapixxDout)\*Demo files for examples.  
  


###See also:
[SetDoutSchedule](Datapixx-SetDoutSchedule), [StopDoutSchedule](Datapixx-StopDoutSchedule), [GetDoutStatus](Datapixx-GetDoutStatus)
