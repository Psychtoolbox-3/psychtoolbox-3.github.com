# [PsychOpenHMDVRCore('Open')](PsychOpenHMDVRCore-Open) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[openhmdPtr, modelName, panelSizeX, panelSizeY, controllerTypes, controllerFlags] = PsychOpenHMDVRCore('Open' [, deviceIndex=0]);

Open connection to [OpenHMD](OpenHMD) controlled VR HMD, return a 'openhmdPtr' handle to  
it.  
  
The call tries to open the HMD with index 'deviceIndex', or the first detected  
HMD, if 'deviceIndex' is omitted. You can pass in a 'deviceIndex' of -1 to open  
an emulated HMD. It doesn't provide any sensor input, but allows some basic  
testing and debugging of VR software nonetheless.  
The returned handle can be passed to the other subfunctions to operate the  
device.  
A second return argument 'modelName' returns the model name string of the  
[OpenHMD](OpenHMD) device.  
'panelSizeX' is the horizontal panel resolution in pixels.  
'panelSizeY' is the vertical panel resolution in pixels.  
'controllerTypes' A bit mask of OVR.[ControllerType](ControllerType)\_XXX flags describing the  
currently connected input controllers.  
'controllerFlags' A bit mask of controller capabilities: +1 = Rotational  
tracking, +2 = Positional tracking, +4 = Haptic feedback.  
  


###See also:
[GetCount](PsychOpenHMDVRCore-GetCount) Close
