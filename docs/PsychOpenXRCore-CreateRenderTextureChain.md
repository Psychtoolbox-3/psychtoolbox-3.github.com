# [PsychOpenXRCore('CreateRenderTextureChain')](PsychOpenXRCore-CreateRenderTextureChain) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

[width, height, numTextures, imageFormat] = PsychOpenXRCore('CreateRenderTextureChain', openxrPtr, eye, width, height, floatFormat, numMSAASamples);

Create texture present chains for [OpenXR](OpenXR) device 'openxrPtr'.  
  
'eye' Eye for which chain should get created: 0 = Left/Mono, 1 = Right.  
If only a chain for eye = 0 is created then the driver operates in monoscopic  
presentation mode for use with [Screen](Screen)() stereomode 0, showing the same mono  
image to both eyes. If a 2nd chain for eye = 1 is created then the driver  
switches to stereoscopic presentation mode for use with [Screen](Screen)() stereomode 12,  
presenting separate images to the left and right eye.  
  
'width' and 'height' are the width x height of the texture into which  
Psychtoolbox [Screen](Screen)() image processing pipeline will render the output image of  
an eye for submission to the XR compositor. Left and right eye must use  
identical 'width' and 'height'.  
  
'floatFormat' Texture format: 0 = RGBA8 sRGB format for sRGB rendering and  
output. 1 = 16 bpc half-float RGBA16F in linear format.  
  
'numMSAASamples' is the number of samples to use per texel. Must be at least 1,  
and can be more on implementations which support MSAA anti-aliasing.  
'numTextures' returns the total number of compositor textures in the swap chain.  
  
Return values are 'width' for selected width of output texture in pixels and  
'height' for height of output texture in pixels.  
  
'imageFormat' is the chosen [OpenGL](OpenGL) internal texture format for the swapchain  
textures.  
  


###See also:
[GetNextTextureHandle](PsychOpenXRCore-GetNextTextureHandle)
