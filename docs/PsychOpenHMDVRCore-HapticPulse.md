# [PsychOpenHMDVRCore('HapticPulse')](PsychOpenHMDVRCore-HapticPulse) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

pulseEndTime = PsychOpenHMDVRCore('HapticPulse', openhmdPtr, controllerType [, duration=2.5][, freq=1.0][, amplitude=1.0]);

Execute a haptic feedback pulse on controller 'controllerType' associated with  
[OpenHMD](OpenHMD) device 'openhmdPtr'.  
  
'duration' is the duration of the pulse in seconds. If omitted, the function  
returns immediately and the default duration of 2.5 seconds is used, unless you  
call the function again with 'freq' = 0, to cancel the currently active pulse.  
Otherwise, if a 'duration' other than 2.5 seconds is specified, the haptic pulse  
executes for the specified duration, and may block execution of your script for  
that time span on some controller types, returning the absolute time when the  
pulse is expected to end.  
  
'freq' Frequency of the vibration in normalized 0.0 - 1.0 range. 0 = Disable  
ongoing pulse immediately.  
  
'amplitude' Normalized amplitude in range 0.0 - 1.0  
  
The return argument 'pulseEndTime' contains the absolute time in seconds when  
the pulse is expected to end, as estimated at the time of calling the function.  
The precision and accuracy of pulse timing is not known.  
  


###See also:

