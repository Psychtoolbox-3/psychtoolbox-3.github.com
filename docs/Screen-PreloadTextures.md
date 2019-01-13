# [Screen('PreloadTextures')](Screen-PreloadTextures) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[resident [texidresident]] = Screen('PreloadTextures', windowPtr [, texids]);

Try to preload textures into VRAM to facilitate fast drawing. This method tries  
to upload textures into the local (and fast) VRAM of your graphics hardware  
before start of trial. This can reduce texture drawing time by avoiding the  
upload delay. "windowPtr" Handle for onscreen window whose textures should be  
preloaded. "texids" is a vector which contains the texture handles of all  
textures which should be preloaded into VRAM. If no vector is given, PTB tries  
to preload all textures into VRAM. The return value 'resident' tells you, if all  
requested textures could be preloaded. A value of 1 means full success. The  
'texidresident' vector tells you for each texture, if that specific texture  
could be preloaded. Preloading requested textures can fail if your gfx-hardware  
has an insufficient amount of free VRAM memory.   


###See also:
[MakeTexture](Screen-MakeTexture) [DrawTexture](Screen-DrawTexture) [GetMovieImage](Screen-GetMovieImage)
