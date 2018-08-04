# [Datapixx('SetMicrophoneSource')](Datapixx-SetMicrophoneSource) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Set Datapixx audio input source.  
-"source" can take on one of two integer values:  
   1: Microphone  
   2: Audio In  
Audio input data can be acquired from two input connectors on the Datapixx. The  
"MIC IN" jack is a high-impedance microphone input with 2V bias. This is for  
unpowered microphones, as might be found on an inexpensive headset. The "Audio  
IN" jack is a line level (1V RMS) audio input for connection to powered  
microphones, or any standard line out (1V RMS) audio equipment.  
-"gain" specifies the amplication (1-1000) which is applied to the input signal.  
If the optional gain parameter is not supplied, default values are 100 for the  
microphone input, and 1 for the line-level audio input.  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule)
