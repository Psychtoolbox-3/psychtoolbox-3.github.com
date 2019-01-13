# [Datapixx('SetDinLog')](Datapixx-SetDinLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetDinLog' [, bufferBaseAddress=12e6] [, numBufferFrames=1000]);

Configure digital input transition logging. The log reports rising and falling  
edges of the digital inputs, with associated timetags, and is the best way to  
monitor button box responses or read parallel port data.  
-"bufferBaseAddress" specifies the start of the RAM buffer which should hold the  
logged data inside the Datapixx. Use [ReadDinLog](ReadDinLog) to upload the logged data from  
this address after calling [StartDinLog](StartDinLog).  
-"numBufferFrames" specifies the desired size of the log buffer in the Datapixx  
RAM. This buffer is circular, so it must be large enough to hold all logged  
transitions between successive calls to [ReadDinLog](ReadDinLog). newLogFrames returned by  
[GetDinStatus](GetDinStatus) indicates the number of transitions logged since the last call to  
[ReadDinLog](ReadDinLog).  
Note that the first call to [StartDinLog](StartDinLog) must be preceeded by a call to [SetDinLog](SetDinLog)  
to initialize and clear the log. Once [SetDinLog](SetDinLog) has been called, [StartDinLog](StartDinLog) and  
[StopDinLog](StopDinLog) may be called multiple times to enable and disable logging.  
Note that logged timetags are implemented in hardware with microsecond  
precision.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[EnableDinDebounce](Datapixx-EnableDinDebounce), [StartDinLog](Datapixx-StartDinLog), [StopDinLog](Datapixx-StopDinLog), [GetDinStatus](Datapixx-GetDinStatus), [ReadDinLog](Datapixx-ReadDinLog)
