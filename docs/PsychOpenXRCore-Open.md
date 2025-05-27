# [PsychOpenXRCore('Open')](PsychOpenXRCore-Open) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[openxrPtr, modelName, runtimeName, hasEyeTracking, hasHandTracking] = PsychOpenXRCore('Open' [, deviceIndex=0]);

Open connection to [OpenXR](OpenXR) device, return a 'openxrPtr' handle to it.  
  
The call tries to open the device with index 'deviceIndex', or the first  
detected device if 'deviceIndex' is omitted. Please note that currently only one  
single device is supported by [OpenXR](OpenXR)-1, so this 'deviceIndex' is redundant at  
the moment, given that zero is the only valid value.  
The returned handle can be passed to the other subfunctions to operate the  
device.  
'modelName' returns the model name string of the [OpenXR](OpenXR) device.  
'runtimeName' returns the name of the [OpenXR](OpenXR) runtime.  
'hasEyeTracking' returns the level of eye tracking support: 0 = None, 1 = Basic.  
'hasHandTracking' returns the level of hand tracking support: 0 = None, 1 =  
Basic.  
  


###See also:
[GetCount](PsychOpenXRCore-GetCount) Close
