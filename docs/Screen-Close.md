# [Screen('Close')](Screen-Close) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


[Close](Close) an onscreen or offscreen window or a texture. If the optional  
windowOrTextureIndex isn't provided, then all textures and offscreen windows are  
closed/deleted while regular onscreen windows are left open. If you want to  
close a subset of your offscreen windows or textures, but not all of them you  
can also pass in a vector of texture/offscreen window handles and all handles in  
the vector will be closed.   


###See also:
[OpenWindow](Screen-OpenWindow), [OpenOffscreenWindow](Screen-OpenOffscreenWindow)
