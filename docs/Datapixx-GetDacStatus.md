# [Datapixx('GetDacStatus')](Datapixx-GetDacStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns a struct containing the following DAC status information:  
-"scheduleRunning" is 1 if DAC waveform playback schedule is currently running,  
or 0 if stopped.  
-"scheduleOnset" is the programmed delay in seconds between [StartDacSchedule](StartDacSchedule)  
execution, and the first DAC update.  
-"scheduleRate" is the rate at which the generated waveform is sampled.  
-"scheduleRateUnits" is the programmed units of scheduleRate:  
   1: samples per second  
   2: samples per video frame  
   3: seconds per sample  
-"numChannels" is the number of DAC channels in the schedule and buffer.  
-"channelString" is a string with one status character per DAC channel. If the  
channel is not scheduled, the character is '-'; otherwise, the status character  
is the channel number (eg: '0--3' means that channels 0 and 3 are scheduled).  
-"bufferBaseAddress" is the waveform data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the waveform data buffer.  
-"numBufferFrames" is the total number of samples which fit in the waveform data  
buffer specified in [SetDacSchedule](SetDacSchedule).  
-"currentWriteFrame" is the buffer frame which will be written by the next  
streaming call to [WriteDacBuffer](WriteDacBuffer).  
-"currentReadFrame" is the current buffer frame being read by the [DACs](DACs)  
-"freeBufferFrames" = numBufferFrames - (currentWriteFrame - currentReadFrame).  
This is the maximum number of frames which can be written by the next call to  
[WriteDacBuffer](WriteDacBuffer) in streaming mode, without causing a streaming overflow.  
-"maxScheduleFrames", if non-0, is the value of currentReadFrame which will  
automatically stop the schedule.  
-"numStreamUnderflows" is the number of [WriteDacBuffer](WriteDacBuffer) streaming underflows  
which have occurred since [SetDacSchedule](SetDacSchedule). See [WriteDacBuffer](WriteDacBuffer) for details.  
-"numStreamOverflows" is the number of [WriteDacBuffer](WriteDacBuffer) streaming overflows which  
have occurred since [SetDacSchedule](SetDacSchedule). See [WriteDacBuffer](WriteDacBuffer) for details.  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[SetDacSchedule](Datapixx-SetDacSchedule), [StartDacSchedule](Datapixx-StartDacSchedule), [StopDacSchedule](Datapixx-StopDacSchedule), [WriteDacBuffer](Datapixx-WriteDacBuffer)
