# [PsychPortAudio('SetOpMode')](PsychPortAudio-SetOpMode) 
##### [Psychtoolbox](Psychtoolbox)>[PsychPortAudio](PsychPortAudio).{mex*} subfunction


Override basic mode of operation of an open audio device 'pahandle' and/or  
return old/current mode.  
The device must be open for this setting to take effect and operations must be  
stopped. If the device isn't stopped, it will be forcefully stopped. The  
current/old opMode is returned in the optional return value 'oldOpMode'.  
'opModeOverride' is the optional new opMode: At device open time, the initial  
opMode is assigned via the 'mode' parameter of [PsychPortAudio](PsychPortAudio)('Open', ...); and  
defaults to audio playback if omitted.  
  
The mode can only be changed within certain constraints. It is not possible to  
switch a device from playback to capture mode, or from simplex to full-duplex  
mode after it has been opened. It is possible to change other special opMode  
flags though, e.g., one can enable/disable the live (software based) low-latency  
monitoring mode of full-duplex devices by adding or not adding the value '4' to  
the opMode value.  
  
The function will ignore settings that can't be changed while the device is  
open.  
  


###See also:
Start Stop [RescheduleStart](PsychPortAudio-RescheduleStart) Open Close
