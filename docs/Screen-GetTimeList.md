# [Screen('GetTimeList')](Screen-GetTimeList) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

timeList= Screen('GetTimelist');

Return a vector of doubles holding times as reported by [GetSecs](GetSecs).  When debugging  
is enabled for particular  [Screen](Screen) subfunctions using a [Screen](Screen) preference  
setting, diagnostics may store time values in an array held by [Screen](Screen).  
[GetTimelist](GetTimelist) returns that array. The array is cleared by using the [Screen](Screen)  
'ClearTimeList' command.  


###See also:
[ClearTimeList](Screen-ClearTimeList)
