# [Datapixx('GetAudioGroupDelay')](Datapixx-GetAudioGroupDelay) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns Datapixx Audio OUT group delay in seconds.  
This is the time between when a schedule sends a data sample to the CODEC, and  
when that sample has greatest output at the "Audio OUT" jack of the Datapixx.  
Due to the way in which [CODECs](CODECs) operate, this delay is a function of the sample  
rate. For greatest precision in audio stimulus timing, this value could be  
subtracted from the scheduleOnset parameter before calling [SetAudioSchedule](SetAudioSchedule).  
See [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) for an example.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetAudioSchedule](Datapixx-SetAudioSchedule)
