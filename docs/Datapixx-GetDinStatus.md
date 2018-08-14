# [Datapixx('GetDinStatus')](Datapixx-GetDinStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Returns a struct containing the following digital input status information:  
-"doutDinLoopback" is 1 if digital inputs are driven internally by digital  
outputs, or 0 if digital inputs report real inputs from db-25 connector.  
-"dataDirection" is a mask showing which of the 24 bits are driving their  
outputs.  
-"dataOutStrength" is the drive strength for the ports whose outputs have been  
enabled by [SetDinDataDirection](SetDinDataDirection).  
-"debounce" is 1 if digital inputs are debounced for 30 milliseconds.  
-"logRunning" is 1 if transition logging is currently active, or 0 if stopped.  
-"bufferBaseAddress" is the acquisition data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the acquisition data buffer.  
-"numBufferFrames" is the total number of samples which fit in the acquisition  
data buffer.  
-"currentWriteFrame" is the buffer frame which will be written by the next  
acquired sample.  
-"currentReadFrame" is the buffer frame which will be read by the next call to  
[ReadDinLog](ReadDinLog).  
-"newLogFrames" = currentWriteFrame - currentReadFrame. This is the maximum  
number of frames which can be read by the next call to [ReadDinLog](ReadDinLog), without  
causing an underflow.  
-"numLogUnderflows" is the number of [ReadDinLog](ReadDinLog) underflows which have occurred  
since [SetDinLog](SetDinLog). See [ReadDinLog](ReadDinLog) for details.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[SetDinLog](Datapixx-SetDinLog), [StartDinLog](Datapixx-StartDinLog), [StopDinLog](Datapixx-StopDinLog), [ReadDinLog](Datapixx-ReadDinLog)
