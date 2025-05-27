# [PsychOpenXRCore('GetNextTextureHandle')](PsychOpenXRCore-GetNextTextureHandle) 
##### [Psychtoolbox](Psychtoolbox)>[PsychOpenXRCore](PsychOpenXRCore).{mex*} subfunction

texObjectHandle = PsychOpenXRCore('GetNextTextureHandle', openxrPtr, eye);

Retrieve [OpenGL](OpenGL) texture object handle for next target texture for [OpenXR](OpenXR) device  
'openxrPtr'.  
'eye' Eye for which handle of next texture should be returned: 0 = Left/Mono, 1  
= Right.  
Returns a GL\_TEXTURE\_2D texture object name/handle in 'texObjectHandle' for the  
texture to which the next XR frame should be rendered. Returns -1 if busy.  
  


###See also:
[CreateRenderTextureChain](PsychOpenXRCore-CreateRenderTextureChain)
