# [PsychOpenXRCore('GetFovTextureSize')](PsychOpenXRCore-GetFovTextureSize) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[width, height, recMSAASamples, maxMSAASamples, maxWidth, maxHeight] = PsychOpenXRCore('GetFovTextureSize', openxrPtr, eye);

Return recommended size of client renderbuffers for [OpenXR](OpenXR) device 'openxrPtr'.  
'eye' which eye to provide the size for: 0 = Left, 1 = Right.  
Return values are 'width' for recommended width of framebuffer in pixels and  
'height' for recommended height of framebuffer in pixels.  
'recMSAASamples' is the recommended number of samples per pixel for MSAA  
anti-aliasing, where a value greater than one means to use MSAA.  
'maxMSAASamples' is the maximum MSAA sample count supported by the runtime.  
'maxWidth' and 'maxHeight' are the maximum width and height of the framebuffer  
in pixels, as supported by the runtime.  
  


###See also:

