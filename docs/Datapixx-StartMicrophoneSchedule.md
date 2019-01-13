# [Datapixx('StartMicrophoneSchedule')](Datapixx-StartMicrophoneSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StartMicrophoneSchedule');

Start running an audio acquisition schedule. The actual hardware schedule will  
be initiated by the next [RegWr](RegWr)\* command, and then the audio inputs will acquire  
their first sample after the scheduleOnset specified in [SetMicrophoneSchedule](SetMicrophoneSchedule).  
Note that every call to [StartMicrophoneSchedule](StartMicrophoneSchedule) must be preceeded by a call to  
[SetMicrophoneSchedule](SetMicrophoneSchedule) (ie: multiple calls to [StartMicrophoneSchedule](StartMicrophoneSchedule) each  
require their own call to [SetMicrophoneSchedule)](SetMicrophoneSchedule)).  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo and [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) files for examples.  
  


###See also:
[SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule), [StopMicrophoneSchedule](Datapixx-StopMicrophoneSchedule), [GetMicrophoneStatus](Datapixx-GetMicrophoneStatus), [ReadMicrophoneBuffer](Datapixx-ReadMicrophoneBuffer)
