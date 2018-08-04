# [PsychOculusVRCore('GetStaticRenderParameters')](PsychOculusVRCore-GetStaticRenderParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOculusVRCore](PsychOculusVRCore).{mex*} subfunction


Retrieve static rendering parameters for Oculus device 'oculusPtr' at current  
settings.  
'clipNear' Optional near clipping plane for [OpenGL](OpenGL). Defaults to 0.01.  
'clipFar' Optional far clipping plane for [OpenGL](OpenGL). Defaults to 10000.0.  
  
### Return arguments:  
  
'projL' is the 4x4 [OpenGL](OpenGL) projection matrix for the left eye rendering.  
'projR' is the 4x4 [OpenGL](OpenGL) projection matrix for the right eye rendering.  
Please note that projL and projR are usually identical for typical rendering  
scenarios.  
  


###See also:

