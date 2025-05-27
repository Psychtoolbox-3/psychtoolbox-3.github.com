# [PsychOpenXRCore('HapticPulse')](PsychOpenXRCore-HapticPulse) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

pulseEndTime = PsychOpenXRCore('HapticPulse', openxrPtr, controllerType [, duration=2.5][, freq][, amplitude=1.0]);

Request execution of a haptic feedback pulse on controller 'controllerType'  
associated with [OpenXR](OpenXR) device 'openxrPtr'.  
  
The function will return immediately, but depending on [OpenXR](OpenXR) runtime will only  
take effect at some later point in time. E.g., the Oculus runtime on MS-Windows  
will only take action at the next [Screen](Screen)('[Flip](Flip)'). This is unfortunate.  
  
'duration' is the duration of the pulse in seconds. If 'duration' is omitted, a  
default duration of 2.5 seconds is used. If a 'duration' is specified, the  
function requests use of that duration. A duration of 0 is mapped to a runtime +  
hardware specific minimum duration, e.g., 0.1 seconds is a common minimum  
duration. Please note that depending on runtime and hardware, there might also  
be a maximum duration to which 'duration' will be clamped by the runtime. E.g.,  
Oculus touch controllers under the Oculus [OpenXR](OpenXR) runtime for Microsoft Windows  
will not execute a haptic feedback pulse longer than 2.5 seconds.  
  
'freq' Requested frequency of the vibration: 'freq' is understood to be in Hz  
for 'freq' \> 1, or in a normalized 0.0 - 1.0 range:  
0 = Disable ongoing pulse immediately.  
0 < freq <= 1 will be mapped to 0 Hz to 320 Hz for compatibility with other  
older XR api's, runtimes, and Oculus devices.  
freq \> 1 will be passed unchanged as a requested frequency in Hz. The [OpenXR](OpenXR)  
runtimes and devices may clamp freq into a runtime and hardware dependent  
minimum and maximum range, or quantize actual freq to only a few discrete  
supported values. E.g., Oculus CV-1 touch controllers only support 160 Hz and  
320 Hz, whereas Oculus S touch controllers only support 160 Hz and 500 Hz.  
Omitting 'freq' will choose XR\_FREQUENCY\_UNSPECIFIED, which leaves it at the  
discretion of the [OpenXR](OpenXR) runtime to choose some good frequency, for some working  
definition of good.  
  
'amplitude' Normalized amplitude in range 0.0 - 1.0 for vibration strength.  
  
The return argument 'pulseEndTime' contains the absolute time in seconds when  
the pulse is expected to end, as estimated at the time of calling the function.  
The precision and accuracy of pulse timing is runtime dependent ie. may vary.  
Pulses could last shorter or longer than specified and start with some delay,  
depending on system.  
  


###See also:

