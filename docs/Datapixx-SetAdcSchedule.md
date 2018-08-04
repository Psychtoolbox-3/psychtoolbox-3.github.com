# [Datapixx('SetAdcSchedule')](Datapixx-SetAdcSchedule) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Configure a schedule for autonomous ADC analog signal acquisition.  
-"scheduleOnset" is the desired delay (in double precision seconds) between  
schedule initiation, and the first ADC sample acquisition.  
-"scheduleRate" is the rate at which the ADC's acquire successive samples.  
scheduleRate has two formats.  It can be a single number, or a 2 element array.  
If it is a single number, then it specifies integer samples/second. If it is a 2  
element array, then the first element specifies the rate, and the second element  
specifies the units of the rate.  
If units = 1, then the rate is interpreted as integer samples/second.  
If units = 2, then the rate is interpreted as integer samples/video frame.  
If units = 3, then the rate is interpreted as double precision seconds/sample  
(sample period).  
Regardless of the actual format chosen, the resulting sample rate cannot exceed  
200 kHz.  
-"maxScheduleFrames" has two modes, depending on whether the acquisition dataset  
has a fixed known length. If the dataset length is known (eg: 100000 samples),  
then just pass 100000 to maxScheduleFrames. In this mode, once the ADC  
acquisition schedule is started with [StartAdcSchedule](StartAdcSchedule), the schedule will  
terminate automatically when maxScheduleFrames has been acquired. If the dataset  
length is not known in advance, then pass 0 to maxScheduleFrames. In this mode,  
the acquisition will continue until the schedule is manually stopped using  
[StopAdcSchedule](StopAdcSchedule).  
-"channelList" is a 2D matrix of the ADC channels which should be saved to the  
acquisition buffer, and the differential voltage references which should be used  
for each voltage acquired. The first row of the matrix contains 1 or more  
integers in the range 0 to [GetAdcNumChannels](GetAdcNumChannels)-1. This is the list of ADC channels  
which will be acquired. The second row of the matrix indicates the differential  
voltage references for each acquired channel. The reference is selected using a  
code in the range 0-3. Code 0 is used when no differential subtraction is  
required during acquisition. All analog inputs are referenced to ground, also  
known as single-ended acquisition. Code 1 implements fully differential inputs,  
subtracting the adjacent channel's voltage before acquiring (eg: acquiring ADC0  
with code = 1 would subtract the ADC1 voltage from the ADC0 voltage, writing the  
result to the acquisition buffer). When using this mode, data is typically  
acquired only on the even channels, effectively halving the number of available  
channels. Code 2 implements a differential input referenced to the REF0 analog  
input (see the Datapixx user manual for pinouts). This has the benefits of  
high-impedance differential inputs, without having to sacrifice half of the  
channels as with fully differential inputs. Code 3 implements a differential  
input referenced to the REF1 analog input. It is possible to use different codes  
for different analog channels in a single acquisition schedule. For example ADC0  
and ADC1 could be acquired single-ended while ADC2 is referenced to ADC3, and  
ADC4/5/6/7 could be referenced to REF0. It is also possible to pass only a  
single row of ADC channels to channelList. In this case, all of the ADC channels  
will be acquired single-ended.  
-"bufferBaseAddress" specifies the start of the RAM buffer which should hold the  
acquired data inside the Datapixx. Use [ReadAdcBuffer](ReadAdcBuffer) to upload the acquired data  
from this address after calling [StartAdcSchedule](StartAdcSchedule).  
-"numBufferFrames" specifies the desired size of the acquisition buffer in the  
Datapixx RAM. For many applications, the Datapixx has enough RAM to acquire a  
complete dataset without streaming. In these cases, numBufferFrames could be  
left at its default value of maxScheduleFrames. The Datapixx typically has 128  
MB of internal RAM which is shared between all I/O subsystems (DAC/ADC/AUDIO,  
etc). Datapixx('GetRamSize') can be used to query the quantity of RAM in your  
system. If maxScheduleFrames is larger than numBufferFrames (or 0), then each  
time the acquisition frame counter reaches a multiple of numBufferFrames, the  
acquisition buffer address automatically wraps back to bufferBaseAddress. This  
circular buffer effect can be used for acquiring arbitrarily long analog  
datasets. Simply monitor newBufferFrames returned by [GetAdcStatus](GetAdcStatus), and use  
[ReadAdcBuffer](ReadAdcBuffer) in streaming mode to upload newly acquired data from the Datapixx  
RAM to the host.  
Note that every call to [StartAdcSchedule](StartAdcSchedule) must be preceeded by a call to  
[SetAdcSchedule](SetAdcSchedule) (ie: multiple calls to [StartAdcSchedule](StartAdcSchedule) each require their own  
call to [SetAdcSchedule)](SetAdcSchedule)).  
Note that schedule timing is implemented in hardware with microsecond precision.  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[StartAdcSchedule](Datapixx-StartAdcSchedule), [StopAdcSchedule](Datapixx-StopAdcSchedule), [GetAdcStatus](Datapixx-GetAdcStatus), [ReadAdcBuffer](Datapixx-ReadAdcBuffer)
