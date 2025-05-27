# [PsychOpenXRCore('GetStaticRenderParameters')](PsychOpenXRCore-GetStaticRenderParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[projL, projR, fovL, fovR] = PsychOpenXRCore('GetStaticRenderParameters', openxrPtr [, clipNear=0.01][, clipFar=10000.0]);

Retrieve static rendering parameters for [OpenXR](OpenXR) device 'openxrPtr' at current  
settings.  
'clipNear' Optional near clipping plane for [OpenGL](OpenGL). Defaults to 0.01.  
'clipFar' Optional far clipping plane for [OpenGL](OpenGL). Defaults to 10000.0.  
  
### Return arguments:  
  
'projL' is the 4x4 [OpenGL](OpenGL) projection matrix for the left eye rendering.  
'projR' is the 4x4 [OpenGL](OpenGL) projection matrix for the right eye rendering.  
Please note that projL and projR are usually identical for typical rendering  
scenarios.  
'fovL' is the [leftAngle, rightAngle, upAngle, downAngle] field of view for the  
left eye rendering.  
'fovR' is the [leftAngle, rightAngle, upAngle, downAngle] field of view for the  
right eye rendering.  
fovL and fovR angles are in units of radians, from the optical axis.  
  


###See also:

