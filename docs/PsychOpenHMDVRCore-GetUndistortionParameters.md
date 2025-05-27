# [PsychOpenHMDVRCore('GetUndistortionParameters')](PsychOpenHMDVRCore-GetUndistortionParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[width, height, hmdShiftx, hmdShifty, hmdShiftz, abberation, distortion, scrnHorSize, scrnVertSize] = PsychOpenHMDVRCore('GetUndistortionParameters', openhmdPtr, eye [, inputWidth][, inputHeight][, fov]);

Return parameters needed for rendering and undistortion for [OpenHMD](OpenHMD) device  
'openhmdPtr'.  
'eye' which eye to provide the data: 0 = Left, 1 = Right.  
'inputWidth' = Width of the rendered input image buffer in pixels.  
'inputHeight' = Height of the rendered input image buffer in pixels.  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. You can pass in the 'fovPort' value returned from  
[PsychOpenHMDVR](PsychOpenHMDVR)('GetFovTextureSize'); Defaults to whatever has been set for the  
given eye in the last call to [PsychOpenHMDVR](PsychOpenHMDVR)('GetFovTextureSize'); if omitted.  
  
Return values:  
[width, height] = Width and height of client renderbuffers in pixels. Same as  
the provided 'inputWidth' and 'inputHeight'.  
[hmdShiftx, hmdShifty, hmdShiftz] = [HmdToEyeViewOffset](HmdToEyeViewOffset) 3D translation vector.  
Defines the location of the optical center of the eye relative to the origin of  
the local head reference frame, ie. the tracked head position.  
abberation = 3-component vector with optical lens color abberation correction  
coefficients.  
distortion = 4-component vector with optical lens geometric distortion  
correction coefficients.  
scrnHorSize = Horizontal screen size in meters.  
scrnVertSize = Vertical screen size in meters.  
  
  


###See also:
[GetFovTextureSize](PsychOpenHMDVRCore-GetFovTextureSize)
