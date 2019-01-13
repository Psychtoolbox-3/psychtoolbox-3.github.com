# [Screen('OpenProxy')](Screen-OpenProxy) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

proxyPtr = Screen('OpenProxy', windowPtr [, imagingmode]);

Create a proxy object. A proxy is a windowRecord (like a texture, offscreen  
window or onscreen window), but without associated image content. Its useful as  
a container for all the typical settings associated with a window or texture.  
Its main purpose is to store additional hook function chains for use with the  
imaging pipeline. The users script can create special proxy objects for  
different image processing subtasks, attach proper user defined hook chains to  
it, and then switch between different hook chains by simply passing different  
proxy objects to the image processing functions. This way we are not limited to  
a fixed number of imaging hooks but can create new ones dynamically. Read 'help  
PsychGLImageProcessing' for more infos about proxies and the pipeline.   
  
'windowPtr' is a handle to an associated parent onscreen window. Just pass the  
handle of the onscreen window for which image processing is supposed to take  
place. The routine returns a handle 'proxyPtr' to the new proxy object. You can  
delete proxy objects via the regular [Screen](Screen)('[Close](Close)', proxyPtr) or  
[Screen](Screen)('CloseAll'); command as you would do with textures or windows. You can  
add or modify hook functions by passing the 'proxyPtr' to the  
[Screen](Screen)('Hookfunction', ...) subfunction. You can apply a proxy via the  
[Screen](Screen)('TransformTexture') function. 'imagingmode' flags to define the boundary  
conditions for image processing.   


###See also:
Hookfunction, [TransformTexture](Screen-TransformTexture)
