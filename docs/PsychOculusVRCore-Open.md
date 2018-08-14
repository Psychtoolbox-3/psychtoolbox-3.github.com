# [PsychOculusVRCore('Open')](PsychOculusVRCore-Open) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction


Open connection to Oculus VR HMD, return a 'oculusPtr' handle to it.  
  
The call tries to open the HMD with index 'deviceIndex', or the first detected  
HMD, if 'deviceIndex' is omitted. You can pass in a 'deviceIndex' of -1 to open  
an emulated HMD. It doesn't provide any sensor input, but allows some basic  
testing and debugging of VR software nonetheless.  
The returned handle can be passed to the other subfunctions to operate the  
device.  
A second return argument 'modelName' returns the model name string of the Oculus  
device.  
  


###See also:
[GetCount](PsychOculusVRCore-GetCount) Close
