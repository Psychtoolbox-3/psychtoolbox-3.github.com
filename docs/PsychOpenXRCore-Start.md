# [PsychOpenXRCore('Start')](PsychOpenXRCore-Start) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

PsychOpenXRCore('Start', openxrPtr);

Start user-script driven head orientation and position tracking operation on  
[OpenXR](OpenXR) device 'openxrPtr'.  
  
The driver assumes that the user-script runs a tight/fast animation loop with  
appropriate calls to the head tracking functions, to drive driver internal  
tracking state updates and inform the rendering. Too slowly running user-script  
animation loops, stopped animation loops or loops avoiding the needed calls to  
the 'GetTrackingState', ie., [PsychVRHMD](PsychVRHMD)('PrepareRender'), function, may cause  
visual artifacts in the device's presented imagery, e.g., judder and jerks.  


###See also:
Stop [GetTrackingState](PsychOpenXRCore-GetTrackingState)
