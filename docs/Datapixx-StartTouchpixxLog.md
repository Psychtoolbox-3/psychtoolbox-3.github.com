# [Datapixx('StartTouchpixxLog')](Datapixx-StartTouchpixxLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Start logging [TOUCHPixx](TOUCHPixx) touch panel activity. The [TOUCHPixx](TOUCHPixx) controller polls the  
panel at more than 5kHz waiting for a panel press. When a panel press is  
detected, a touch timetag is stored with the x,y coordinates into the log buffer  
specified by [SetTouchpixxLog](SetTouchpixxLog). If continuous logging is enabled, successive  
timetags and coordinates are logged at 200Hz. A final timetag and (0,0)  
coordinates are logged when the panel pressure is released. newLogFrames  
returned by [GetTouchpixxStatus](GetTouchpixxStatus) indicates the number of transitions logged since  
the last call to [ReadTouchpixxLog](ReadTouchpixxLog).  
Note that the first call to [StartTouchpixxLog](StartTouchpixxLog) must be preceeded by a call to  
[SetTouchpixxLog](SetTouchpixxLog) to initialize and clear the log. Once [SetTouchpixxLog](SetTouchpixxLog) has been  
called, [StartTouchpixxLog](StartTouchpixxLog) and [StopTouchpixxLog](StopTouchpixxLog) may be called multiple times to  
enable and disable logging.  
Note that the [TOUCHPixx](TOUCHPixx) subsystem uses some of the Digital Input resources.  
Specifically, [TOUCHPixx](TOUCHPixx) logging cannot be used simultaneously with digital input  
logging.  
See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [SetTouchpixxLog](Datapixx-SetTouchpixxLog), [StopTouchpixxLog](Datapixx-StopTouchpixxLog), [ReadTouchpixxLog](Datapixx-ReadTouchpixxLog), [EnableTouchpixxLogContinuousMode](Datapixx-EnableTouchpixxLogContinuousMode), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
