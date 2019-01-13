# [Datapixx('SetTouchpixxLog')](Datapixx-SetTouchpixxLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('SetTouchpixxLog' [, bufferBaseAddress=12e6] [, numBufferFrames=1000]);

Configure [TOUCHPixx](TOUCHPixx) touch panel logging. The [TOUCHPixx](TOUCHPixx) controller polls the  
panel at more than 5kHz waiting for a panel press. When a panel press is  
detected, a touch timetag is stored with the x,y coordinates into a log buffer.  
If continuous logging is enabled, successive timetags and coordinates are logged  
at 200Hz. A final timetag and (0,0) coordinates are logged when the panel  
pressure is released.  
-"bufferBaseAddress" specifies the start of the RAM buffer which should hold the  
logged data inside the Datapixx. Use [ReadTouchpixxLog](ReadTouchpixxLog) to upload the logged data  
from this address after calling [StartTouchpixxLog](StartTouchpixxLog).  
-"numBufferFrames" specifies the desired size of the log buffer in the Datapixx  
RAM. This buffer is circular, so it must be large enough to hold all logged  
transitions between successive calls to [ReadTouchpixxLog](ReadTouchpixxLog). newLogFrames returned  
by [GetTouchpixxStatus](GetTouchpixxStatus) indicates the number of transitions logged since the last  
call to [ReadTouchpixxLog](ReadTouchpixxLog).  
Note that the first call to [StartTouchpixxLog](StartTouchpixxLog) must be preceeded by a call to  
[SetTouchpixxLog](SetTouchpixxLog) to initialize and clear the log. Once [SetTouchpixxLog](SetTouchpixxLog) has been  
called, [StartTouchpixxLog](StartTouchpixxLog) and [StopTouchpixxLog](StopTouchpixxLog) may be called multiple times to  
enable and disable logging.  
Note that the [TOUCHPixx](TOUCHPixx) subsystem uses some of the Digital Input resources.  
Specifically, [TOUCHPixx](TOUCHPixx) logging cannot be used simultaneously with digital input  
logging.  
See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [StartTouchpixxLog](Datapixx-StartTouchpixxLog), [StopTouchpixxLog](Datapixx-StopTouchpixxLog), [ReadTouchpixxLog](Datapixx-ReadTouchpixxLog), [EnableTouchpixxLogContinuousMode](Datapixx-EnableTouchpixxLogContinuousMode), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
