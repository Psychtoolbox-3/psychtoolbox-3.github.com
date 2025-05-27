# [PsychOpenXRCore('Controllers')](PsychOpenXRCore-Controllers) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

controllerTypes = PsychOpenXRCore('Controllers', openxrPtr);

Return currently available and active controllers for [OpenXR](OpenXR) device 'openxrPtr'.  
The returned 'controllerTypes' can be the logical OR of one of these flags:  
OVR.[ControllerType](ControllerType)\_LTouch = Left touch controller (Left tracked hand).  
OVR.[ControllerType](ControllerType)\_RTouch = Right touch controller (Right tracked hand).  
OVR.[ControllerType](ControllerType)\_Remote = Connected remote control or similar, e.g., control  
buttons on a HMD.  
OVR.[ControllerType](ControllerType)\_XBox = Microsoft [XBox](XBox) controller or some equivalent gamepad.  
  
  


###See also:
[GetInputState](PsychOpenXRCore-GetInputState) [HapticPulse](PsychOpenXRCore-HapticPulse)
