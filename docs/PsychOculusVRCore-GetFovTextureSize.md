# [PsychOculusVRCore('GetFovTextureSize')](PsychOculusVRCore-GetFovTextureSize) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction

[width, height, fovPort] = PsychOculusVRCore('GetFovTextureSize', oculusPtr, eye [, fov=[HMDRecommended]][, pixelsPerDisplay=1]);

Return recommended size of client renderbuffers for Oculus device 'oculusPtr'.  
'eye' which eye to provide the size for: 0 = Left, 1 = Right.  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. If 'fov' is omitted, the Oculus runtime will be asked for a  
good default field of view and that will be used. The field of view may be  
dependent on the settings in the Oculus user profile of the currently selected  
user.  
'pixelsPerDisplay' Ratio of the number of render target pixels to display pixels  
at the center of distortion. Defaults to 1.0 if omitted. Lower values can  
improve performance, at lower quality.  
  
Return values are 'width' for minimum recommended width of framebuffer in pixels  
and 'height' for minimum recommended height of framebuffer in pixels. 'fovPort'  
is the field of view in degrees finally used for calculation of 'width' x  
'height'.  
  


###See also:
[GetUndistortionParameters](PsychOculusVRCore-GetUndistortionParameters)
