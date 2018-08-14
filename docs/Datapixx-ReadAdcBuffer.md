# [Datapixx('ReadAdcBuffer')](Datapixx-ReadAdcBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Upload ADC data from a Datapixx internal acquisition buffer to the local host.  
-"numFrames" is the number of acquired frames to upload. In a streaming  
application, numFrames should not exceed newBufferFrames returned by  
[GetAdcStatus](GetAdcStatus). It may be possible to reduce dynamic memory allocation overhead by  
matching numFrames to the size of an existing bufferData output argument.  
-"bufferAddress" is the byte address in Datapixx RAM where the buffered data can  
be found. If this argument is not provided, it will take on the value of  
bufferBaseAddress passed to the last call to [SetAdcSchedule](SetAdcSchedule). Specifying a  
bufferAddress of -1 will cause data to be streamed from the buffer which was  
defined in the last call to [SetAdcSchedule](SetAdcSchedule).  
-"bufferData" is a 2D matrix of acquired ADC voltages. Each row of the matrix  
contains the acquired data for one ADC channel. Each column of the matrix  
contains one acquired datum for each ADC channel. [ReadAdcBuffer](ReadAdcBuffer) assumes that the  
number of channels to return equals the number of channels passed in the last  
call to [SetAdcSchedule](SetAdcSchedule).  
-"bufferTimetags" is a row vector of acquisition timetags. There is one timetag  
for each acquisition frame in bufferData. The timetags are in double precision  
seconds since Datapixx powerup.  
-"underflow" or "overflow" are set to 1 if streaming calls to [ReadAdcBuffer](ReadAdcBuffer) read  
data too quickly or too slowly. If bufferAddress is passed a value of -1, then  
[ReadAdcBuffer](ReadAdcBuffer) is streaming continuous acquisition data from a circular buffer.  
Streaming acquisition must ensure that the uploaded data frame always remains  
behind the acquisition frame, without allowing acquired data to overflow the  
acquisition buffer. The newBufferFrames field returned by [GetAdcStatus](GetAdcStatus) indicates  
the maximum number of frames which can be read by [ReadAdcBuffer](ReadAdcBuffer). If more than  
this number of frames is read, an underflow occurs and there will be errors in  
the acquired data. If the streaming data is not read quickly enough, and  
newBufferFrames exceeds the buffer size (numBufferFrames passed to  
[SetAdcSchedule)](SetAdcSchedule)) then an overflow has occurred, causing data to be lost. In  
addition to returning underflow/overflow flags, the  
numStreamUnderflows/numStreamOverflows fields returned by [GetAdcStatus](GetAdcStatus) will be  
incremented.  
See [DatapixxAdc](DatapixxAdc)\*Demo files for examples.  
  


###See also:
[SetAdcSchedule](Datapixx-SetAdcSchedule), [StartAdcSchedule](Datapixx-StartAdcSchedule), [StopAdcSchedule](Datapixx-StopAdcSchedule), [GetAdcStatus](Datapixx-GetAdcStatus)
