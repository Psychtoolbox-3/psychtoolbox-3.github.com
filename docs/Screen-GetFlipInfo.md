# [Screen('GetFlipInfo')](Screen-GetFlipInfo) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

info = Screen('GetFlipInfo', windowPtr [, infoType=0] [, auxArg1]);

Returns a struct with miscellaneous info about finished flips on the specified  
onscreen window.  
  
This function is currently only supported on Linux X11/GLX with the free  
graphics drivers,  
and on Linux/Wayland with support for the presentation\_feedback extension.  
  
The function allows you to enable logging of timestamps and other status  
information about all completed bufferswaps, as triggered via [Screen](Screen)('[Flip](Flip)'),  
[Screen](Screen)('AsyncFlipBegin') etc. Whenever a flip completes, a little info struct is  
stored in a internal queue. This function allows you to fetch these info structs  
from the queue. It allows you to enable and disable logging of these info  
structs. Logging is disabled by default.  
  
"windowPtr" is the handle of the onscreen window for which info should be  
returned.  
"infoType" If left out or set to zero, the flip handle for the last invocation  
of flip is returned. E.g., if a value of 53 is returned, then the info struct  
with a info.[SwapbuffersCount](SwapbuffersCount) field of 53 will contain the info for that last  
invocation of flip.  
This allows to associate specific flips with the returned logged timestamps and  
other info.  
If set to 1, logging of flip completion info is enabled.  
If set to 2, logging of flip completion info is disabled.  
If set to 3, the oldest stored flip completion info is returned in a struct  
'info'.  
  
# The info struct contains the following fields  
  
[OnsetTime](OnsetTime): Visual stimulus onset time of the completed [Screen](Screen)('[Flip](Flip)') operation.  
[OnsetVBLCount](OnsetVBLCount): Video refresh cycle count when the flip completed.  
[SwapbuffersCount](SwapbuffersCount): Serial number of this info struct. Corresponds to the handle  
returned for 'infoType' zero.  
[SwapType](SwapType): How was the flip executed? Low level info about strategy chosen by  
GPU.  
[BackendFeedbackString](BackendFeedbackString): A string with more info, which is specific to a display  
backend, e.g., GLX vs. Wayland.  
Note: Currently only flips with a 'SwapType' field containing the (sub-)string  
'Pageflip' are considered to have reliable timing and trustworthy timestamps. On  
Wayland dislay servers a 'SwapType' of 'ImpreciseCopy' also has good timing,  
although likely with less precise and accurate onset timestamps.  
'ImprecisePageflip' is also considered having slightly less precise and accurate  
onset timestamps. Other types of 'Pageflip's should be high quality in the time  
domain.  
  
  


###See also:
[OpenWindow](Screen-OpenWindow), Flip, [NominalFrameRate](Screen-NominalFrameRate)
