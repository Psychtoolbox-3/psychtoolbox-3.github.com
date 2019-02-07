# [Screen('TransformTexture')](Screen-TransformTexture) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

transtexid = Screen('TransformTexture', sourceTexture, transformProxyPtr [, sourceTexture2][, targetTexture] [, specialFlags]);

Apply an image processing operation to a texture 'sourceTexture' and store the  
processed result either in 'targetTexture' if provided, or in a new texture (if  
'targetTexture' is not provided). Use the data in the optional 'sourceTexture2'  
as well if provided. This could be, e.g., a lookup table or a 2nd image for  
stereo processing. Return a handle 'transtexid' to the processed texture.  
If 'targetTexture' was provided and suitable then the returned 'transtexid' will  
be identical to 'targetTexture'. For maximum efficiency in iterative processing,  
you should hand the 'transtexid' from a previous call to  
[Screen](Screen)('TransformTexture') back into a successive call as 'targetTexture', so  
the same container can be recycled. At first invocation you could hand in an  
empty [] 'targetTexture' to leave optimal choice of the format to the function.  
If you want to hand your self-made 'targetTexture' then using a handle created  
via [Screen](Screen)('OpenOffscreenWindow') will be slightly more efficient than using a  
handle created via [Screen](Screen)('MakeTexture').  
The image processing operation is defined in the processing hook chain  
'UserDefinedBlit' of the proxy object 'transformProxyPtr'.  
'specialFlags' optional flags to alter operation of this function:  
kPsychAssumeTextureNormalized - Assume source texture(s) are already in a  
normalized upright orientation. This can speed up processing, but it can lead to  
wrong results if the textures are not normalized and the imaging operation is  
non-isotropic - Use with care. A setting of specialFlags == 2 will ask to create  
or set the resulting 'transtexid' texture for high-precision drawing, see same  
setting in [Screen](Screen)('MakeTexture') for explanation.  
Read 'help PsychGLImageProcessing' for more infos on how to use this function.  


###See also:

