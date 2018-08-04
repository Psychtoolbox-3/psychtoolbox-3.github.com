# [Datapixx('StartAudioSchedule')](Datapixx-StartAudioSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Start running an audio waveform playback schedule. The actual hardware schedule  
will be initiated by the next [RegWr](RegWr)\* command, and then the first waveform sample  
will play after the scheduleOnset specified in [SetAudioSchedule](SetAudioSchedule).  
Note that every call to [StartAudioSchedule](StartAudioSchedule) must be preceeded by a call to  
[SetAudioSchedule](SetAudioSchedule) (ie: multiple calls to [StartAudioSchedule](StartAudioSchedule) each require their  
own call to [SetAudioSchedule)](SetAudioSchedule)).  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxAudio](DatapixxAudio)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetAudioSchedule](Datapixx-SetAudioSchedule), [StopAudioSchedule](Datapixx-StopAudioSchedule), [GetAudioStatus](Datapixx-GetAudioStatus)
