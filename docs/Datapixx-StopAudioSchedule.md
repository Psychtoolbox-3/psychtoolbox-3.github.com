# [Datapixx('StopAudioSchedule')](Datapixx-StopAudioSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Stop running an audio waveform playback schedule. The actual hardware schedule  
will be terminated by the next [RegWr](RegWr)\* command.  
Note that if maxScheduleFrames was assigned a non-0 value in [SetAudioSchedule](SetAudioSchedule),  
then the schedule can be left to terminate automatically without having to call  
[StopAudioSchedule](StopAudioSchedule).  
See [DatapixxAudio](DatapixxAudio)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetAudioSchedule](Datapixx-SetAudioSchedule), [StartAudioSchedule](Datapixx-StartAudioSchedule), [GetAudioStatus](Datapixx-GetAudioStatus)
