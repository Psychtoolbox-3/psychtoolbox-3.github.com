# [PsychOpenXRCore('Stop')](PsychOpenXRCore-Stop) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

PsychOpenXRCore('Stop', openxrPtr);

Stop user-script driven head orientation and position tracking operation on  
[OpenXR](OpenXR) device 'openxrPtr'.  
  
This signals that the user-scripts animation loop is (about to be) stopped, will  
run at low framerate, and/or avoid calls to 'GetTrackingState', ie.,  
[PsychVRHMD](PsychVRHMD)('PrepareRender'). This means the script will not take care of the  
processing needed to keep tracked 3D content displaying properly. The driver  
will try to take care of needed steps itself to provide a stable picture in the  
device display in this case, if possible, given the used hardware + [OpenXR](OpenXR) and  
operating system software setup. Results may vary...  
  


###See also:
Start [GetTrackingState](PsychOpenXRCore-GetTrackingState)
