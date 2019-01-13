# [Datapixx('GetAudioStatus')](Datapixx-GetAudioStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

status = Datapixx('GetAudioStatus');

Returns a struct containing the following audio status information:  
-"scheduleRunning" is 1 if audio waveform playback schedule is currently  
running, or 0 if stopped.  
-"scheduleOnset" is the programmed delay in seconds between [StartAudioSchedule](StartAudioSchedule)  
execution, and the first audio update.  
-"scheduleRate" is the audio sample rate in samples per second.  
-"lrMode" is the left/right ear update mode (see [SetAudioSchedule](SetAudioSchedule) for details).  
-"volumeAudioOutLeft" is the volume of the left channel routed to the Audio Out  
jack.  
-"volumeAudioOutRight" is the volume of the right channel routed to the Audio  
Out jack.  
-"volumeSpeakerLeft" is the volume of the left channel routed to the internal  
speaker.  
-"volumeSpeakerRight" is the volume of the right channel routed to the internal  
speaker.  
-"bufferBaseAddress" is the waveform data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the waveform data buffer.  
-"numBufferFrames" is the total number of audio samples which fit in the  
waveform data buffer specified in [SetAudioSchedule](SetAudioSchedule).  
-"currentWriteFrame" is the buffer frame which will be written by the next  
streaming call to [WriteAudioBuffer](WriteAudioBuffer).  
-"currentReadFrame" is the current buffer frame being read by the audio  
transmitter  
-"freeBufferFrames" = numBufferFrames - (currentWriteFrame - currentReadFrame).  
This is the maximum number of frames which can be written by the next call to  
[WriteAudioBuffer](WriteAudioBuffer) in streaming mode, without causing a streaming overflow.  
-"maxScheduleFrames", if non-0, is the value of currentReadFrame which will  
automatically stop the schedule.  
-"numStreamUnderflows" is the number of [WriteAudioBuffer](WriteAudioBuffer) streaming underflows  
which have occurred since [SetAudioSchedule](SetAudioSchedule). See [WriteAudioBuffer](WriteAudioBuffer) for details.  
-"numStreamOverflows" is the number of [WriteAudioBuffer](WriteAudioBuffer) streaming overflows  
which have occurred since [SetAudioSchedule](SetAudioSchedule). See [WriteAudioBuffer](WriteAudioBuffer) for details.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxAudio](DatapixxAudio)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetAudioSchedule](Datapixx-SetAudioSchedule), [StartAudioSchedule](Datapixx-StartAudioSchedule), [StopAudioSchedule](Datapixx-StopAudioSchedule), [WriteAudioBuffer](Datapixx-WriteAudioBuffer)
