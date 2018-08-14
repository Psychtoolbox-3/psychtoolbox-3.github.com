# [Datapixx('StopMicrophoneSchedule')](Datapixx-StopMicrophoneSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Stop running an audio acquisition schedule. The actual hardware schedule will be  
terminated by the next [RegWr](RegWr)\* command.  
Note that if maxScheduleFrames was assigned a non-0 value in  
[SetMicrophoneSchedule](SetMicrophoneSchedule), then the schedule can be left to terminate automatically  
without having to call [StopMicrophoneSchedule](StopMicrophoneSchedule).  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo and [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) files for examples.  
  


###See also:
[SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule), [StartMicrophoneSchedule](Datapixx-StartMicrophoneSchedule), [GetMicrophoneStatus](Datapixx-GetMicrophoneStatus)
