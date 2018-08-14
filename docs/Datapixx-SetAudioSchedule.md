# [Datapixx('SetAudioSchedule')](Datapixx-SetAudioSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Configure a schedule for autonomous audio waveform playback.  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and when the first audio waveform sample is played.  
-"scheduleRate" is the rate at which successive waveform samples are sent to the  
audio transmitter. The value is given in samples/second, and must be in the  
range 8000-96000.  
-"maxScheduleFrames" has two modes, depending on whether the full waveform has a  
fixed known length. If the waveform length is known (eg: 100000 samples), then  
just pass 100000 to maxScheduleFrames. In this mode, once the audio waveform  
schedule is started with [StartAudioSchedule](StartAudioSchedule), the schedule will terminate  
automatically when maxScheduleFrames has been reached. If the waveform length is  
not known in advance, then pass 0 to maxScheduleFrames. In this mode, the  
waveform will continue until the schedule is manually stopped using  
[StopAudioSchedule](StopAudioSchedule).  
-"lrMode" specifies how the left/right ears should be updated from the waveform  
buffer. The following values are used:  
   0: MONO,   Each Audio schedule datum goes to left and right ears  
   1: LEFT,   Each Audio schedule datum goes to left ear only  
   2: RIGHT,  Each Audio schedule datum goes to right ear only  
   3: STEREO, Pairs of Audio data go to left/right ears  
If STEREO is selected, then 2 rows of data should be downloaded in  
[WriteAudioBuffer](WriteAudioBuffer). -"bufferBaseAddress" specifies the start of the RAM buffer  
which holds the waveform data inside the Datapixx. Use [WriteAudioBuffer](WriteAudioBuffer) to  
download the audio waveform data to this address before calling  
[StartAudioSchedule](StartAudioSchedule).  
-"numBufferFrames" specifies the size of the waveform buffer in the Datapixx  
RAM. For many applications, the Datapixx has enough RAM for [WriteAudioBuffer](WriteAudioBuffer) to  
download multiple complete waveforms before initiating playback. In these cases,  
numBufferFrames could be left at its default value of maxScheduleFrames. If  
maxScheduleFrames is larger than numBufferFrames (or 0), then each time the  
waveform frame counter reaches a multiple of numBufferFrames, the waveform  
buffer address automatically wraps back to bufferBaseAddress. This circular  
buffer effect can be used for streaming arbitrarily long waveforms into an audio  
schedule. Simply monitor freeBufferFrames returned by [GetAudioStatus](GetAudioStatus), and use  
[WriteAudioBuffer](WriteAudioBuffer) in streaming mode to append new waveform data into buffer space  
which has already been played. The circular buffer effect can also be used to  
implement periodic waveforms very efficiently. A long periodic toneburst could  
be assigned a small buffer filled with only a single period of the waveform. The  
periodic waveform will play continuously, and any [WriteAudioBuff](WriteAudioBuff) into the  
waveform buffer will immediately update the generated waveform.  
Note that every call to [StartAudioSchedule](StartAudioSchedule) must be preceeded by a call to  
[SetAudioSchedule](SetAudioSchedule) (ie: multiple calls to [StartAudioSchedule](StartAudioSchedule) each require their  
own call to [SetAudioSchedule)](SetAudioSchedule)).  
Note that schedule timing is implemented in hardware with microsecond precision.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxAudio](DatapixxAudio)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [WriteAudioBuffer](Datapixx-WriteAudioBuffer), [GetAudioGroupDelay](Datapixx-GetAudioGroupDelay), [StartAudioSchedule](Datapixx-StartAudioSchedule), [StopAudioSchedule](Datapixx-StopAudioSchedule), [GetAudioStatus](Datapixx-GetAudioStatus)
