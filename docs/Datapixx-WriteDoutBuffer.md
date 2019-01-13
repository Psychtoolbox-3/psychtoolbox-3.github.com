# [Datapixx('WriteDoutBuffer')](Datapixx-WriteDoutBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

[nextBufferAddress, underflow, overflow] = Datapixx('WriteDoutBuffer', bufferData [, bufferAddress=8e6]);

Download digital output data from local host to a Datapixx internal digital  
waveform buffer. Digital output waveforms can be used to generate complex  
triggering sequences and any other arbitrary digital waveforms. -"bufferData" is  
a 1D vector of digital output values. Each element of the vector contains new  
values for DOUT bits 0-15. -"bufferAddress" is the byte address in Datapixx RAM  
where the buffer should start. Specifying a bufferAddress of -1 will cause  
bufferData to be streamed to the end of the buffer which was last defined in  
[SetDoutSchedule](SetDoutSchedule), and initialized by a call to [WriteDoutBuffer](WriteDoutBuffer) with bufferAddress  
not set to -1.  
-"nextBufferAddress" is the next Datapixx address after bufferData has been  
downloaded. Multiple contiguous digital waveforms can be downloaded by passing  
the returned nextBufferAddress of one waveform as the bufferAddress of the next  
waveform. The Datapixx typically has 128 MB of internal RAM which is shared  
between all I/O subsystems (DAC/ADC/AUDIO, etc). Datapixx('GetRamSize') can be  
used to query the quantity of RAM in your system.  
-"underflow" or "overflow" are set to 1 if streaming calls to [WriteDoutBuffer](WriteDoutBuffer)  
supply insufficient, or too much, data. If bufferAddress is passed a value of  
-1, then [WriteDoutBuffer](WriteDoutBuffer) is streaming continuous waveform data into a circular  
buffer. Streaming playback must ensure that the provided data always remains  
ahead of the playback position, without providing more data than can fit in the  
playback buffer. The freeBufferFrames field returned by [GetDoutStatus](GetDoutStatus) indicates  
the maximum number of frames which can be written by [WriteDoutBuffer](WriteDoutBuffer). If more  
than this number of frames is written, an overflow occurs and there will be a  
glitch in the generated waveform. If the streaming data is not supplied quickly  
enough, then old data will be played, also causing a glitch. In addition to  
returning underflow/overflow flags, these errors will increment the  
numStreamUnderflows/numStreamOverflows fields returned by [GetDoutStatus](GetDoutStatus).  
See [DatapixxDout](DatapixxDout)\*Demo files for examples.  
  


###See also:
[SetDoutSchedule](Datapixx-SetDoutSchedule)
