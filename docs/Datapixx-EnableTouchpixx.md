# [Datapixx('EnableTouchpixx')](Datapixx-EnableTouchpixx) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

Datapixx('EnableTouchpixx' [, touchPanelMode=0]);

Enable the [TOUCHPixx](TOUCHPixx) touch panel hardware subsystem. The [TOUCHPixx](TOUCHPixx) is either a  
resistive touch panel or a capacitive touch panel. touchPanelMode by default is  
0, which is the value for a resistive touch panel. Set to 1 for a capacitive  
touch panel. It is driven by a custom hardware controller designed by [VPixx](VPixx)  
Technologies. The controller polls the panel at more than 5kHz waiting for a  
panel press. If a press has been detected, its X,Y coordinates can be read with  
[GetTouchpixxCoordinates](GetTouchpixxCoordinates). If logging is enabled, a touch timetag is stored with  
the coordinates into a log buffer. If continuous logging is enabled, successive  
timetags and coordinates are logged at 200Hz. A final timetag and (0,0)  
coordinates are logged when the panel pressure is released.Note that the  
[TOUCHPixx](TOUCHPixx) subsystem uses some of the Digital Input resources. Specifically,  
[TOUCHPixx](TOUCHPixx) logging cannot be used simultaneously with digital input logging.  
See Touchpixx\*Demo files for examples.  
  


###See also:
[DisableTouchpixx](Datapixx-DisableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [SetTouchpixxStabilizeDuration](Datapixx-SetTouchpixxStabilizeDuration), [SetTouchpixxLog](Datapixx-SetTouchpixxLog), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
