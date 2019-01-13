# [Datapixx('EnableAudioLoopback')](Datapixx-EnableAudioLoopback) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('EnableAudioLoopback');

Enable an internal loopback from the audio outputs to the audio inputs. This  
causes sound currently playing on the audio output system to be acquired on the  
audio input system. This convenient feature can be useful when developing audio  
input software.  
Note that when acquiring loopback data, all output volume and input gain  
settings are ignored. The acquired data has exactly the same values as the  
source output data.  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [DisableAudioLoopback](Datapixx-DisableAudioLoopback), [SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule), [GetMicrophoneStatus](Datapixx-GetMicrophoneStatus)
