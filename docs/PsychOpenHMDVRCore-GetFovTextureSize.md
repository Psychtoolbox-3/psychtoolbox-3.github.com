# [PsychOpenHMDVRCore('GetFovTextureSize')](PsychOpenHMDVRCore-GetFovTextureSize) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[width, height, fovPort] = PsychOpenHMDVRCore('GetFovTextureSize', openhmdPtr, eye, metersPerTanAngleAtCenter [, fov=[HMDRecommended]]);

Return recommended size of client renderbuffers for [OpenHMD](OpenHMD) device 'openhmdPtr'.  
'eye' which eye to provide the size for: 0 = Left, 1 = Right.  
'metersPerTanAngleAtCenter' Meters per radians tan angle at the optical center  
of the display. Multiply by a factor \> 1 to improve quality at lower  
performance, < 1 to reduce quality at higher performance.  
'fov' Optional field of view in degrees, from line of sight: [leftdeg, rightdeg,  
updeg, downdeg]. If 'fov' is omitted, the [OpenHMD](OpenHMD) runtime will be asked for a  
good default field of view and that will be used.  
Return values are 'width' for minimum recommended width of framebuffer in pixels  
and 'height' for minimum recommended height of framebuffer in pixels. 'fovPort'  
is the field of view in degrees finally used for calculation of 'width' x  
'height'.  
  


###See also:
[GetUndistortionParameters](PsychOpenHMDVRCore-GetUndistortionParameters)
