# [Datapixx('GetTouchpixxStatus')](Datapixx-GetTouchpixxStatus) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

status = Datapixx('GetTouchpixxStatus');

Returns a struct containing the following [TOUCHPixx](TOUCHPixx) touch panel status  
information:  
-"enabled" is 1 if [TOUCHPixx](TOUCHPixx) touch panel hardware is present and enabled.  
-"touchPanelMode" is 0 for a Resistive touch panel, 1 for a Capacitive touch  
panel.  
-"stabilizeDuration" is duration in seconds that [TOUCHPixx](TOUCHPixx) panel coordinates  
must be stable before being recognized as a touch in [GetTouchpixxCoords](GetTouchpixxCoords)().  
-"isPressed" is 1 if touch panel is currently being pressed.  
-"touchX", "touchY" current touch coordinates.  See [GetTouchpixxCoordinates](GetTouchpixxCoordinates) for  
details.  
-"logRunning" is 1 if [TOUCHPixx](TOUCHPixx) activity is being logged to RAM buffer.  
-"logContinuous" is 1 if continuous position/timetag updates will be logged at  
200Hz during a panel touch, or 0 if logging only returns initial press and  
release events.  
-"bufferBaseAddress" is the acquisition data buffer base address within the  
Datapixx.  
-"bufferSize" is the number of bytes in the acquisition data buffer.  
-"numBufferFrames" is the total number of samples which fit in the acquisition  
data buffer.  
-"currentWriteFrame" is the buffer frame which will be written by the next  
acquired sample.  
-"currentReadFrame" is the buffer frame which will be read by the next call to  
[ReadTouchpixxLog](ReadTouchpixxLog).  
-"newLogFrames" = currentWriteFrame - currentReadFrame. This is the maximum  
number of frames which can be read by the next call to [ReadTouchpixxLog](ReadTouchpixxLog), without  
causing an underflow.  
-"numLogUnderflows" is the number of [ReadTouchpixxLog](ReadTouchpixxLog) underflows which have  
occurred since [SetTouchpixxLog](SetTouchpixxLog). See [ReadTouchpixxLog](ReadTouchpixxLog) for details.  
See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [SetTouchpixxLog](Datapixx-SetTouchpixxLog)
