# [PsychOpenHMDVRCore('GetStaticRenderParameters')](PsychOpenHMDVRCore-GetStaticRenderParameters) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenHMDVRCore](PsychOpenHMDVRCore).{mex*} subfunction

[projL, projR, ipd] = PsychOpenHMDVRCore('GetStaticRenderParameters', openhmdPtr [, clipNear=0.01][, clipFar=10000.0]);

Retrieve static rendering parameters for [OpenHMD](OpenHMD) device 'openhmdPtr' at current  
settings.  
'clipNear' Optional near clipping plane for [OpenGL](OpenGL). Defaults to 0.01.  
'clipFar' Optional far clipping plane for [OpenGL](OpenGL). Defaults to 10000.0.  
  
### Return arguments:  
  
'projL' is the 4x4 [OpenGL](OpenGL) projection matrix for the left eye rendering.  
'projR' is the 4x4 [OpenGL](OpenGL) projection matrix for the right eye rendering.  
'ipd' is estimated inter-pupillar distance.  
Please note that projL and projR are usually identical for typical rendering  
scenarios.  
  


###See also:

