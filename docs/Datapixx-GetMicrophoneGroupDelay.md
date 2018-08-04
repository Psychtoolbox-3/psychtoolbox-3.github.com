# [Datapixx('GetMicrophoneGroupDelay')](Datapixx-GetMicrophoneGroupDelay) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns Datapixx Microphone IN group delay in seconds.  
This is the time between when a voltage appears at the "MIC IN" jack of the  
[DATAPixx](DATAPixx), and when an audio input schedule will acquire the voltage. Due to the  
way in which [CODECs](CODECs) operate, this delay is a function of the sample rate. For  
greatest precision in audio acquisition timing, this value could be subtracted  
from the scheduleOnset parameter before calling [SetMicrophoneSchedule](SetMicrophoneSchedule).  
See [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) for an example.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule)
