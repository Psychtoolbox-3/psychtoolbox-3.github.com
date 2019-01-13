# [Datapixx('SetDacSchedule')](Datapixx-SetDacSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetDacSchedule', scheduleOnset, scheduleRate, maxScheduleFrames [, channelList=0] [, bufferBaseAddress=0] [, numBufferFrames=maxScheduleFrames]);

Configure a schedule for autonomous DAC waveform playback.  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and when the first waveform sample is sent to the [DACs](DACs).  
-"scheduleRate" is the rate at which successive waveform samples are sent to the  
[DACs](DACs). scheduleRate has two formats.  It can be a single number, or a 2 element  
array. If it is a single number, then it specifies integer samples/second. If it  
is a 2 element array, then the first element specifies the rate, and the second  
element specifies the units of the rate.  
If units = 1, then the rate is interpreted as integer samples/second.  
If units = 2, then the rate is interpreted as integer samples/video frame.  
If units = 3, then the rate is interpreted as double precision seconds/sample  
(sample period).  
Regardless of the actual format chosen, the resulting update rate cannot exceed  
1 [MHz](MHz).  
-"maxScheduleFrames" has two modes, depending on whether the full waveform has a  
fixed known length. If the waveform length is known (eg: 100000 samples), then  
just pass 100000 to maxScheduleFrames. In this mode, once the DAC waveform  
schedule is started with [StartDacSchedule](StartDacSchedule), the schedule will terminate  
automatically when maxScheduleFrames has been reached. If the waveform length is  
not known in advance, then pass 0 to maxScheduleFrames. In this mode, the  
waveform will continue until the schedule is manually stopped using  
[StopDacSchedule](StopDacSchedule).  
-"channelList" is a list of the DAC channels which should be updated from the  
waveform buffer. The list should contain 1 or more integers in the range 0 to  
[GetDacNumChannels](GetDacNumChannels)-1.  
The number of scheduled channels should equal the number of channels downloaded  
in [WriteDacBuffer](WriteDacBuffer). -"bufferBaseAddress" specifies the start of the RAM buffer  
which holds the waveform data inside the Datapixx. Use [WriteDacBuffer](WriteDacBuffer) to  
download the waveform data to this address before calling [StartDacSchedule](StartDacSchedule).  
-"numBufferFrames" specifies the size of the waveform buffer in the Datapixx  
RAM. For many applications, the Datapixx has enough RAM for [WriteDacBuffer](WriteDacBuffer) to  
download multiple complete waveforms before initiating playback. In these cases,  
numBufferFrames could be left at its default value of maxScheduleFrames. If  
maxScheduleFrames is larger than numBufferFrames (or 0), then each time the  
waveform frame counter reaches a multiple of numBufferFrames, the waveform  
buffer address automatically wraps back to bufferBaseAddress. This circular  
buffer effect can be used for streaming arbitrarily long waveforms into a DAC  
schedule. Simply monitor freeBufferFrames returned by [GetDacStatus](GetDacStatus), and use  
[WriteDacBuffer](WriteDacBuffer) in streaming mode to append new waveform data into buffer space  
which has already been played. The circular buffer effect can also be used to  
implement periodic waveforms very efficiently. A long periodic toneburst could  
be assigned a small buffer filled with only a single period of the waveform. The  
periodic waveform will play continuously, and any [WriteDacBuff](WriteDacBuff) into the waveform  
buffer will immediately update the generated waveform.  
Note that every call to [StartDacSchedule](StartDacSchedule) must be preceeded by a call to  
[SetDacSchedule](SetDacSchedule) (ie: multiple calls to [StartDacSchedule](StartDacSchedule) each require their own  
call to [SetDacSchedule)](SetDacSchedule)).  
Note that schedule timing is implemented in hardware with microsecond precision.  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[WriteDacBuffer](Datapixx-WriteDacBuffer), [StartDacSchedule](Datapixx-StartDacSchedule), [StopDacSchedule](Datapixx-StopDacSchedule), [GetDacStatus](Datapixx-GetDacStatus)
