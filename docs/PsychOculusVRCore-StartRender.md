# [PsychOculusVRCore('StartRender')](PsychOculusVRCore-StartRender) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction

[eyePoseL, eyePoseR, tracked, frameTiming] = PsychOculusVRCore('StartRender', oculusPtr);

Mark start of a new 3D head tracked render cycle for Oculus device 'oculusPtr'.  
Return values are the vectors which define the two eye cameras positions and  
orientations for the left eye and right eye 'eyePoseL' and 'eyePoseR'. The  
vectors are of form [tx, ty, tz, rx, ry, rz, rw] - A 3 component 3D position  
followed by a 4 component rotation quaternion.  
'tracked' Tracking status flags: 0 = Head not tracked at the moment. 1 = Head  
orientation tracked. 2 = Head position tracked (DK2 and later). 3 = Head  
position and orientation tracked (DK2 and later). 4 = Camera pose tracked, 7 =  
1+2+4 = Camera pose and Head position and orientation tracked.  
  
'frameTiming' Vector with predicted timing information for this frame with  
following elements:  
[1] = [DeltaSeconds](DeltaSeconds) since last frame.  
[2] = [ThisFrameSeconds](ThisFrameSeconds) start of scanout of this frame.  
[3] = [TimewarpPointSeconds](TimewarpPointSeconds)  
[4] = [NextFrameSeconds](NextFrameSeconds)  
[5] = [ScanoutMidpointSeconds](ScanoutMidpointSeconds)  
[6] = [EyeScanoutSeconds](EyeScanoutSeconds)[0]  
[7] = [EyeScanoutSeconds](EyeScanoutSeconds)[1]  
  
  


###See also:
[GetEyePose](PsychOculusVRCore-GetEyePose) [EndFrameTiming](PsychOculusVRCore-EndFrameTiming)
