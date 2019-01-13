# [Datapixx('GetAdcStatus')](Datapixx-GetAdcStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

status = Datapixx('GetAdcStatus');

Returns a struct containing the following ADC status information:  
-"dacAdcLoopback" is 1 if ADC inputs are driven internally by DAC outputs, or 0  
if ADC inputs report real analog inputs.  
-"freeRunning" is 1 if ADC hardware is sampling continuously, or 0 if it only  
samples on ADC acquisition schedule ticks.  
-"scheduleRunning" is 1 if the analog acquisition schedule is currently running,  
or 0 if stopped.  
-"scheduleOnset" is the programmed delay in seconds between [StartAdcSchedule](StartAdcSchedule)  
execution, and the first ADC sample acquisition.  
-"scheduleRate" is the rate at which subsequent ADC samples are acquired.  
-"scheduleRateUnits" is the programmed units of scheduleRate:  
   1: samples per second  
   2: samples per video frame  
   3: seconds per sample  
-"numChannels" is the number of ADC channels scheduled for acquisition.  
-"chanSelString" is a string with one selection status character per ADC  
channel. If the channel is not scheduled, the character is '-'; otherwise, the  
status character is the channel number (eg: '01234567--------' means that  
channels 0 to 7 are stored in the acquisition buffer, but channels 8-15 are  
not).  
-"chanRefString" is a string with one reference status character per ADC  
channel:  
   '-': single ended, referenced to ground  
   'D': fully differential, referenced to adjacent channel  
   '0': differential, referenced to REF0  
   '1': differential, referenced to REF1  
-"bufferBaseAddress" is the acquisition data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the acquisition data buffer.  
-"numBufferFrames" is the total number of samples which fit in the acquisition  
data buffer.  
-"currentWriteFrame" is the buffer frame which will be written by the next  
acquired ADC sample.  
-"currentReadFrame" is the buffer frame which will be read by the next streaming  
call to [ReadAdcBuffer](ReadAdcBuffer).  
-"newBufferFrames" = currentWriteFrame - currentReadFrame. This is the maximum  
number of frames which can be read by the next call to [ReadAdcBuffer](ReadAdcBuffer) in  
streaming mode, without causing a streaming underflow.  
-"maxScheduleFrames", if non-0, is the value of currentWriteFrame which will  
automatically stop the schedule.  
-"numStreamUnderflows" is the number of [ReadAdcBuffer](ReadAdcBuffer) streaming underflows which  
have occurred since [SetAdcSchedule](SetAdcSchedule). See [ReadAdcBuffer](ReadAdcBuffer) for details.  
-"numStreamOverflows" is the number of [ReadAdcBuffer](ReadAdcBuffer) streaming overflows which  
have occurred since [SetAdcSchedule](SetAdcSchedule). See [ReadAdcBuffer](ReadAdcBuffer) for details.  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[SetAdcSchedule](Datapixx-SetAdcSchedule), [StartAdcSchedule](Datapixx-StartAdcSchedule), [StopAdcSchedule](Datapixx-StopAdcSchedule), [ReadAdcBuffer](Datapixx-ReadAdcBuffer)
