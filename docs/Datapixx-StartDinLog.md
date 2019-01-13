# [Datapixx('StartDinLog')](Datapixx-StartDinLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('StartDinLog');

Start logging transitions of digital input bits 0 to 15. This will log rising  
and falling edges of the digital inputs, and is the best way to monitor button  
box responses. Whenever a transition is detected, the log will receive a new  
record containing the timetag of the transition, and the new state of the  
digital inputs. The actual hardware logging will be initiated by the next [RegWr](RegWr)\*  
command.  
Note that the first call to [StartDinLog](StartDinLog) must be preceeded by a call to [SetDinLog](SetDinLog)  
to initialize and clear the log. Once [SetDinLog](SetDinLog) has been called, [StartDinLog](StartDinLog) and  
[StopDinLog](StopDinLog) may be called multiple times to enable and disable logging.  
See [DatapixxSimonGame](DatapixxSimonGame), [DatapixxDin](DatapixxDin)\*Demo files for examples.  
  


###See also:
[EnableDinDebounce](Datapixx-EnableDinDebounce), [SetDinLog](Datapixx-SetDinLog), [StopDinLog](Datapixx-StopDinLog), [GetDinStatus](Datapixx-GetDinStatus), [ReadDinLog](Datapixx-ReadDinLog)
