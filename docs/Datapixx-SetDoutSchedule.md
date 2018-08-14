# [Datapixx('SetDoutSchedule')](Datapixx-SetDoutSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Configure a schedule for autonomous TTL digital output waveform playback.  
Digital output schedules drive bits DOUT0-DOUT15 on the "Digital OUT" db-25  
connector. Digital output waveforms can be used to generate complex triggering  
sequences and any other arbitrary digital waveforms.  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and when the first waveform sample is sent to the digital  
outputs.  
-"scheduleRate" is the rate at which successive waveform samples are sent to the  
digital outputs. scheduleRate has two formats.  It can be a single number, or a  
2 element array. If it is a single number, then it specifies integer  
samples/second. If it is a 2 element array, then the first element specifies the  
rate, and the second element specifies the units of the rate.  
If units = 1, then the rate is interpreted as integer samples/second.  
If units = 2, then the rate is interpreted as integer samples/video frame.  
If units = 3, then the rate is interpreted as double precision seconds/sample  
(sample period).  
Regardless of the actual format chosen, the resulting update rate cannot exceed  
10 [MHz](MHz).  
-"maxScheduleFrames" has two modes, depending on whether the full waveform has a  
fixed known length. If the waveform length is known (eg: 100000 samples), then  
just pass 100000 to maxScheduleFrames. In this mode, once the digital waveform  
schedule is started with [StartDoutSchedule](StartDoutSchedule), the schedule will terminate  
automatically when maxScheduleFrames has been reached. If the waveform length is  
not known in advance, then pass 0 to maxScheduleFrames. In this mode, the  
waveform will continue until the schedule is manually stopped using  
[StopDoutSchedule](StopDoutSchedule).  
-"bufferBaseAddress" specifies the start of the RAM buffer which holds the  
waveform data inside the Datapixx. Use [WriteDoutBuffer](WriteDoutBuffer) to download the waveform  
data to this address before calling [StartDoutSchedule](StartDoutSchedule).  
-"numBufferFrames" specifies the size of the waveform buffer in the Datapixx  
RAM. For many applications, the Datapixx has enough RAM for [WriteDoutBuffer](WriteDoutBuffer) to  
download multiple complete waveforms before initiating playback. In these cases,  
numBufferFrames could be left at its default value of maxScheduleFrames. If  
maxScheduleFrames is larger than numBufferFrames (or 0), then each time the  
waveform frame counter reaches a multiple of numBufferFrames, the waveform  
buffer address automatically wraps back to bufferBaseAddress. This circular  
buffer effect can be used for streaming arbitrarily long waveforms into a  
digital output schedule. Simply monitor freeBufferFrames returned by  
[GetDoutStatus](GetDoutStatus), and use [WriteDoutBuffer](WriteDoutBuffer) in streaming mode to append new waveform  
data into buffer space which has already been played. The circular buffer effect  
can also be used to implement periodic waveforms very efficiently. A periodic  
clock output could be generated with a buffer filled with only 2 samples; one  
high and one low. The resulting clock output will run continuously.  
Note that every call to [StartDoutSchedule](StartDoutSchedule) must be preceeded by a call to  
[SetDoutSchedule](SetDoutSchedule) (ie: multiple calls to [StartDoutSchedule](StartDoutSchedule) each require their own  
call to [SetDoutSchedule)](SetDoutSchedule)).  
Note that schedule timing is implemented in hardware with microsecond precision.  
See [DatapixxDout](DatapixxDout)\*Demo files for examples.  
  


###See also:
[WriteDoutBuffer](Datapixx-WriteDoutBuffer), [StartDoutSchedule](Datapixx-StartDoutSchedule), [StopDoutSchedule](Datapixx-StopDoutSchedule), [GetDoutStatus](Datapixx-GetDoutStatus)
