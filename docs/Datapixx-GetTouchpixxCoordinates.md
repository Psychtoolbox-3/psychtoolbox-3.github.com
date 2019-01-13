# [Datapixx('GetTouchpixxCoordinates')](Datapixx-GetTouchpixxCoordinates) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction

coordinates = Datapixx('GetTouchpixxCoordinates');

Returns 2-element vector containing [TOUCHPixx](TOUCHPixx) x/y location currently being  
touched. Each of the x/y coordinates ranges from 0 to 1. The coordinate space  
origin is the top-left corner of the touch panel. If the panel is not currently  
being touched, (0,0) will be returned. [SetTouchpixxStabilizeDuration](SetTouchpixxStabilizeDuration) can specify  
a minimal required touch duration. See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [SetTouchpixxStabilizeDuration](Datapixx-SetTouchpixxStabilizeDuration), [SetTouchpixxLog](Datapixx-SetTouchpixxLog), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
