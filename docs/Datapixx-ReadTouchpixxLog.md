# [Datapixx('ReadTouchpixxLog')](Datapixx-ReadTouchpixxLog) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Upload [TOUCHPixx](TOUCHPixx) touch panel activity from a Datapixx internal log buffer to the  
local host.  
-"numFrames" is the number of frames to upload, and should not exceed  
newLogFrames returned by [GetTouchpixxStatus](GetTouchpixxStatus). If numFrames argument is missing,  
[ReadTouchpixxLog](ReadTouchpixxLog) will return all remaining logged data.  
-"logCoords" is a 2D array with 2 rows containing x/y touch coordinates, and one  
column for each touch datum. Each of the x/y coordinates ranges from 0 to 1. The  
coordinate space origin is the top-left corner of the touch panel. When the  
panel stops being touched, (0,0) will be returned.  
-"logTimetags" is a row vector of acquisition timetags, indicating when the  
corresponding touch or release in logData occurred. The timetags are in double  
precision seconds since Datapixx powerup. Response times can be calculated by  
calling [SetMarker](SetMarker)() at stimulus onset, then subtracting [GetMarker](GetMarker)() from the  
logged timetags.  
-"underflow" is set to 1 if calls to [ReadTouchpixxLog](ReadTouchpixxLog) read too many frames. The  
newLogFrames field returned by [GetTouchpixxStatus](GetTouchpixxStatus) indicates the maximum number  
of frames which can be read by [ReadTouchpixxLog](ReadTouchpixxLog). If more than this number of  
frames is read, an underflow occurs and there will be errors in the logged data.  
In addition to returning an underflow flag, the numLogUnderflows field returned  
by [GetTouchpixxStatus](GetTouchpixxStatus) will be incremented.  
See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [SetTouchpixxLog](Datapixx-SetTouchpixxLog), [StartTouchpixxLog](Datapixx-StartTouchpixxLog), [StopTouchpixxLog](Datapixx-StopTouchpixxLog), [EnableTouchpixxLogContinuousMode](Datapixx-EnableTouchpixxLogContinuousMode), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
