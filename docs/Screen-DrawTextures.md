# [Screen('DrawTextures')](Screen-DrawTextures) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Draw many textures at once, either one texture to many locations or many  
textures.  
This function accepts the same parameters as [Screen](Screen)('DrawTexture'), but it is  
optimized for drawing many textures. You can leave out each argument, a default  
setting will be used in that case, provide it once to apply it to all drawn  
items, or provide a vector or matrix with a individual setting for each drawn  
item. If you provide multiple settings per argument, then the number must match  
between all arguments.  
  
Examples:  
a) One texture drawn to different locations at different orientations: Provide  
one texture handle for the texturePointer, a 4 row by n columns matrix for  
'destinationRect' to provide target rectangles for n locations, provide a n  
component vector of 'rotationAngles' for the n different orientations of the n  
drawn texture patches.  
b) n textures drawn to n different locations: Same as a) but provide a n  
component vector of 'texturePointers' one for each texture to be drawn to one of  
n locations at n angles.  
  


###See also:
[MakeTexture](Screen-MakeTexture) [DrawTexture](Screen-DrawTexture) [DrawTextures](Screen-DrawTextures)
