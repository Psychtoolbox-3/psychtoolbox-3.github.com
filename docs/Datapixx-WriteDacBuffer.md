# [Datapixx('WriteDacBuffer')](Datapixx-WriteDacBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

[nextBufferAddress, underflow, overflow] = Datapixx('WriteDacBuffer', bufferData [, bufferAddress=0] [, channelList=[0:numChannels-1]]);

Download DAC data from local host to a Datapixx internal waveform buffer.  
-"bufferData" is a 2D matrix of DAC waveform voltages. Each row of the matrix  
contains the sample data for one DAC channel. Each column of the matrix contains  
one sample for each DAC channel.  
-"bufferAddress" is the byte address in Datapixx RAM where the buffer should  
start. Specifying a bufferAddress of -1 will cause bufferData to be streamed to  
the end of the buffer which was last defined in [SetDacSchedule](SetDacSchedule), and initialized  
by a call to [WriteDacBuffer](WriteDacBuffer) with bufferAddress not set to -1.  
-"nextBufferAddress" is the next Datapixx address after bufferData has been  
downloaded. Multiple contiguous waveforms can be downloaded by passing the  
returned nextBufferAddress of one waveform as the bufferAddress of the next  
waveform. The Datapixx typically has 128 MB of internal RAM which is shared  
between all I/O subsystems (DAC/ADC/AUDIO, etc). Datapixx('GetRamSize') can be  
used to query the quantity of RAM in your system.  
-"channelList" is an optional list of the DAC channels which will be targeted by  
the waveform buffer. channelList is only used for looking up the DAC voltage  
ranges in order to convert double precision bufferData into binary DAC data.  
channelList defaults to [0:numChannels-1], where numChannels is the number of  
rows in bufferData.  
-"underflow" or "overflow" are set to 1 if streaming calls to [WriteDacBuffer](WriteDacBuffer)  
supply insufficient, or too much, data. If bufferAddress is passed a value of  
-1, then [WriteDacBuffer](WriteDacBuffer) is streaming continuous waveform data into a circular  
buffer. Streaming playback must ensure that the provided data always remains  
ahead of the playback position, without providing more data than can fit in the  
playback buffer. The freeBufferFrames field returned by [GetDacStatus](GetDacStatus) indicates  
the maximum number of frames which can be written by [WriteDacBuffer](WriteDacBuffer). If more  
than this number of frames is written, an overflow occurs and there will be a  
glitch in the generated waveform. If the streaming data is not supplied quickly  
enough, then old data will be played, also causing a glitch. In addition to  
returning underflow/overflow flags, these errors will increment the  
numStreamUnderflows/numStreamOverflows fields returned by [GetDacStatus](GetDacStatus).  
See [DatapixxDac](DatapixxDac)\*Demo files for examples.  
  


###See also:
[SetDacSchedule](Datapixx-SetDacSchedule)
