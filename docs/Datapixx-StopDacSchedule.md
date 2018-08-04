# [Datapixx('StopDacSchedule')](Datapixx-StopDacSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Stop running a DAC waveform playback schedule. The actual hardware schedule will  
be terminated by the next [RegWr](RegWr)\* command.  
Note that if maxScheduleFrames was assigned a non-0 value in [SetDacSchedule](SetDacSchedule),  
then the schedule can be left to terminate automatically without having to call  
[StopDacSchedule](StopDacSchedule).  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[SetDacSchedule](Datapixx-SetDacSchedule), [StartDacSchedule](Datapixx-StartDacSchedule), [GetDacStatus](Datapixx-GetDacStatus)
