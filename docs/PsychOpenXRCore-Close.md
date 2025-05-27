# [PsychOpenXRCore('Close')](PsychOpenXRCore-Close) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

PsychOpenXRCore('Close' [, openxrPtr]);

[Close](Close) connection to [OpenXR](OpenXR) device 'openxrPtr' if that device is open and active.  
If the optional 'openxrPtr' is omitted, then close all open devices. Once the  
last open device has been closed, shutdown the driver, ie. perform the same  
cleanup as if 'clear PsychOpenXRCore' would be executed.  
  


###See also:
Open
