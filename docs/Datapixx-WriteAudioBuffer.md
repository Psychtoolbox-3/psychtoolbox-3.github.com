# [Datapixx('WriteAudioBuffer')](Datapixx-WriteAudioBuffer) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Download audio data from local host to a Datapixx internal waveform buffer.  
-"bufferData" is a 2D matrix of audio waveform data in the range -1 to +1. The  
first row of the matrix contains data for the left ear, and the second row  
contains data for the right-ear. A mono dataset will only have a single row.  
-"bufferAddress" is the byte address in Datapixx RAM where the buffer should  
start. Specifying a bufferAddress of -1 will cause bufferData to be streamed to  
the end of the buffer which was last defined in [SetAudioSchedule](SetAudioSchedule), and  
initialized by a call to [WriteAudioBuffer](WriteAudioBuffer) with bufferAddress not set to -1.  
-"nextBufferAddress" is the next Datapixx address after bufferData has been  
downloaded. Multiple contiguous audio waveforms can be downloaded by passing the  
returned nextBufferAddress of one waveform as the bufferAddress of the next  
waveform. The Datapixx typically has 128 MB of internal RAM which is shared  
between all I/O subsystems (DAC/ADC/AUDIO, etc). Datapixx('GetRamSize') can be  
used to query the quantity of RAM in your system.  
-"underflow" or "overflow" are set to 1 if streaming calls to [WriteAudioBuffer](WriteAudioBuffer)  
supply insufficient, or too much, data. If bufferAddress is passed a value of  
-1, then [WriteAudioBuffer](WriteAudioBuffer) is streaming continuous waveform data into a circular  
buffer. Streaming playback must ensure that the provided data always remains  
ahead of the playback position, without providing more data than can fit in the  
playback buffer. The freeBufferFrames field returned by [GetAudioStatus](GetAudioStatus) indicates  
the maximum number of columns which can be written by [WriteAudioBuffer](WriteAudioBuffer). If more  
than this number of frames is written, an overflow occurs and there will be a  
glitch in the generated waveform. If the streaming data is not supplied quickly  
enough, then old data will be played, also causing a glitch. In addition to  
returning underflow/overflow flags, these errors will increment the  
numStreamUnderflows/numStreamOverflows fields returned by [GetAudioStatus](GetAudioStatus).  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxAudio](DatapixxAudio)\*Demo files for examples.  
  


###See also:
[InitAudio](Datapixx-InitAudio), [SetAudioSchedule](Datapixx-SetAudioSchedule)
