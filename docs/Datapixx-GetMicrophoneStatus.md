# [Datapixx('GetMicrophoneStatus')](Datapixx-GetMicrophoneStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns a struct containing the following audio input status information:  
-"source" is the audio input source:  
   0: Has not been set yet via [SetMicrophoneSource](SetMicrophoneSource)  
   1: High impedance "MIC IN" jack  
   2: Line level "Audio IN" jack  
-"gain" is the input audio amplification set by [SetMicrophoneSource](SetMicrophoneSource)  
-"audioLoopback" is 1 if audio inputs are driven internally by audio outputs, or  
0 if audio inputs decode sound from external input jacks.  
-"scheduleRunning" is 1 if the audio acquisition schedule is currently running,  
or 0 if stopped.  
-"scheduleOnset" is the programmed delay in seconds between  
[StartMicrophoneSchedule](StartMicrophoneSchedule) execution, and the first audio sample acquisition.  
-"scheduleRate" is the audio sample rate in samples per second.  
-"lrMode" is the left/right ear acquisition mode (see [SetMicrophoneSchedule](SetMicrophoneSchedule) for  
details).  
-"bufferBaseAddress" is the acquisition data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the acquisition data buffer.  
-"numBufferFrames" is the total number of samples which fit in the acquisition  
data buffer.  
-"currentWriteFrame" is the buffer frame which will be written by the next  
acquired audio sample.  
-"currentReadFrame" is the buffer frame which will be read by the next streaming  
call to [ReadMicrophoneBuffer](ReadMicrophoneBuffer).  
-"newBufferFrames" = currentWriteFrame - currentReadFrame. This is the maximum  
number of frames which can be read by the next call to [ReadMicrophoneBuffer](ReadMicrophoneBuffer) in  
streaming mode, without causing a streaming underflow.  
-"maxScheduleFrames", if non-0, is the value of currentWriteFrame which will  
automatically stop the schedule.  
-"numStreamUnderflows" is the number of [ReadMicrophoneBuffer](ReadMicrophoneBuffer) streaming  
underflows which have occurred since [SetMicrophoneSchedule](SetMicrophoneSchedule). See  
[ReadMicrophoneBuffer](ReadMicrophoneBuffer) for details.  
-"numStreamOverflows" is the number of [ReadMicrophoneBuffer](ReadMicrophoneBuffer) streaming overflows  
which have occurred since [SetMicrophoneSchedule](SetMicrophoneSchedule). See [ReadMicrophoneBuffer](ReadMicrophoneBuffer) for  
details.  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo and [DatapixxAudioFeedbackDemo](DatapixxAudioFeedbackDemo) files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule), [StartMicrophoneSchedule](Datapixx-StartMicrophoneSchedule), [StopMicrophoneSchedule](Datapixx-StopMicrophoneSchedule), [ReadMicrophoneBuffer](Datapixx-ReadMicrophoneBuffer)
