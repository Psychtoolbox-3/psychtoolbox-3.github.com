# [Datapixx('GetDoutStatus')](Datapixx-GetDoutStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns a struct containing the following digital output status information:  
-"buttonSchedules" is 1 if DIN button presses cause automatic DOUT schedules.  
-"backlightPulse" is 1 if LCD backlight LED enables are gated by DOUT15.  
-"scheduleRunning" is 1 if digital output waveform playback schedule is  
currently running, or 0 if stopped.  
-"scheduleOnset" is the programmed delay in seconds between [StartDoutSchedule](StartDoutSchedule)  
execution, and the first TTL output update.  
-"scheduleRate" is the rate at which the generated waveform is sampled.  
-"scheduleRateUnits" is the programmed units of scheduleRate:  
   1: samples per second  
   2: samples per video frame  
   3: seconds per sample  
-"bufferBaseAddress" is the waveform data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the waveform data buffer.  
-"numBufferFrames" is the total number of samples which fit in the waveform data  
buffer specified in [SetDoutSchedule](SetDoutSchedule).  
-"currentWriteFrame" is the buffer frame which will be written by the next  
streaming call to [WriteDoutBuffer](WriteDoutBuffer).  
-"currentReadFrame" is the current buffer frame being sent to the digital  
outputs  
-"freeBufferFrames" = numBufferFrames - (currentWriteFrame - currentReadFrame).  
This is the maximum number of frames which can be written by the next call to  
[WriteDoutBuffer](WriteDoutBuffer) in streaming mode, without causing a streaming overflow.  
-"maxScheduleFrames", if non-0, is the value of currentReadFrame which will  
automatically stop the schedule.  
-"numStreamUnderflows" is the number of [WriteDoutBuffer](WriteDoutBuffer) streaming underflows  
which have occurred since [SetDoutSchedule](SetDoutSchedule). See [WriteDoutBuffer](WriteDoutBuffer) for details.  
-"numStreamOverflows" is the number of [WriteDoutBuffer](WriteDoutBuffer) streaming overflows which  
have occurred since [SetDoutSchedule](SetDoutSchedule). See [WriteDoutBuffer](WriteDoutBuffer) for details.  
See [DatapixxDout](DatapixxDout)\*Demo files for examples.  
  


###See also:
[SetDoutSchedule](Datapixx-SetDoutSchedule), [StartDoutSchedule](Datapixx-StartDoutSchedule), [StopDoutSchedule](Datapixx-StopDoutSchedule), [WriteDoutBuffer](Datapixx-WriteDoutBuffer)
