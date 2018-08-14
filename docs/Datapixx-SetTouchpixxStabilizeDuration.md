# [Datapixx('SetTouchpixxStabilizeDuration')](Datapixx-SetTouchpixxStabilizeDuration) 
##### [Psychtoolbox](Psychtoolbox)>[Datapixx](Datapixx).{mex*} subfunction


Set duration in seconds that [TOUCHPixx](TOUCHPixx) panel coordinates must be stable before  
being recognized as a touch in [GetTouchpixxCoordinates](GetTouchpixxCoordinates). Touching a resistive  
panel very lightly with a soft object (eg: finger) can cause some jitter in the  
panel's calculated x/y touch coordinates. To eliminate this jitter in data  
returned by [GetTouchpixxCoordinates](GetTouchpixxCoordinates), we can specify a period of time within  
which measured x/y coordinates must be stable before being recognised as a  
touch. The initial value for this parameter is 0, which will return unfiltered  
x/y coordinates. A reasonable value would be 0.01 (10 milliseconds). Note that  
this feature only affects coordinates returned by [GetTouchpixxCoordinates](GetTouchpixxCoordinates).  
Values returned by logging are never filtered. The stabilization is implemented  
in software, so [GetTouchpixxCoordinates](GetTouchpixxCoordinates) must be called repetitively during the  
stabilization period. See Touchpixx\*Demo files for examples.  
  


###See also:
[EnableTouchpixx](Datapixx-EnableTouchpixx), [GetTouchpixxCoordinates](Datapixx-GetTouchpixxCoordinates), [SetTouchpixxLog](Datapixx-SetTouchpixxLog), [GetTouchpixxStatus](Datapixx-GetTouchpixxStatus)
