# [Datapixx('ReadMicrophoneBuffer')](Datapixx-ReadMicrophoneBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Upload audio input data from a Datapixx internal acquisition buffer to the local  
host.  
-"numFrames" is the number of acquired frames to upload. In a streaming  
application, numFrames should not exceed newBufferFrames returned by  
[GetMicrophoneStatus](GetMicrophoneStatus). It may be possible to reduce dynamic memory allocation  
overhead by matching numFrames to the size of an existing bufferData output  
argument.  
-"bufferAddress" is the byte address in Datapixx RAM where the buffered data can  
be found. If this argument is not provided, it will take on the value of  
bufferBaseAddress passed to the last call to [SetMicrophoneSchedule](SetMicrophoneSchedule). Specifying a  
bufferAddress of -1 will cause data to be streamed from the buffer which was  
defined in the last call to [SetMicrophoneSchedule](SetMicrophoneSchedule).  
-"bufferData" is a 2D matrix of acquired audio input data in the range -1 to +1.  
The first row of the matrix contains data for the left ear, and the second row  
contains data for the right ear. A non-stereo dataset will only have a single  
row. [ReadMicrophoneBuffer](ReadMicrophoneBuffer) assumes that the number of channels to return equals  
the number of channels specified by lrMode in the last call to  
[SetMicrophoneSchedule](SetMicrophoneSchedule).  
-"underflow" or "overflow" are set to 1 if streaming calls to  
[ReadMicrophoneBuffer](ReadMicrophoneBuffer) read data too quickly or too slowly. If bufferAddress is  
passed a value of -1, then [ReadMicrophoneBuffer](ReadMicrophoneBuffer) is streaming continuous  
acquisition data from a circular buffer. Streaming acquisition must ensure that  
the uploaded data frame always remains behind the acquisition frame, without  
allowing acquired data to overflow the acquisition buffer. The newBufferFrames  
field returned by [GetMicrophoneStatus](GetMicrophoneStatus) indicates the maximum number of frames  
which can be read by [ReadMicrophoneBuffer](ReadMicrophoneBuffer). If more than this number of frames is  
read, an underflow occurs and there will be errors in the acquired data. If the  
streaming data is not read quickly enough, and newBufferFrames exceeds the  
buffer size (numBufferFrames passed to [SetMicrophoneSchedule)](SetMicrophoneSchedule)) then an overflow  
has occurred, causing data to be lost. In addition to returning  
underflow/overflow flags, the numStreamUnderflows/numStreamOverflows fields  
returned by [GetMicrophoneStatus](GetMicrophoneStatus) will be incremented.  
See [DatapixxMicrophone](DatapixxMicrophone)\*Demo files for examples.  
  


###See also:
[SetMicrophoneSchedule](Datapixx-SetMicrophoneSchedule), [StartMicrophoneSchedule](Datapixx-StartMicrophoneSchedule), [StopMicrophoneSchedule](Datapixx-StopMicrophoneSchedule), [GetMicrophoneStatus](Datapixx-GetMicrophoneStatus)
