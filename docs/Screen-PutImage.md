# [Screen('PutImage')](Screen-PutImage) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('PutImage', windowPtr, imageArray [,rect])

Copy the matrix "imageArray" to a window, very slowly.  
This function is not (and will not ever get) supported on [OpenGL](OpenGL)-ES embedded  
graphics hardware.  
"rect" is in window coordinates. The whole image is copied to "rect", scaling if  
necessary. The rect default is the imageArray's rect, centered in the window.  
The orientation of the array in the window is identical to that of Matlab's  
numerical array displays in the Command Window. The first pixel is in the upper  
left, and the rows are horizontal. imageArray can be a pure luminance matrix, a  
RGB color matrix, or a RGBA color matrix with alpha channel. Its data type can  
be uint8 (faster) or double. Please note that this function is relatively slow  
and inflexible. Have a look at the 'MakeTexture' and 'DrawTexture' functions for  
a faster and more flexible way of drawing image matrices.   


###See also:
[GetImage](Screen-GetImage) [OpenOffscreenWindow](Screen-OpenOffscreenWindow) [MakeTexture](Screen-MakeTexture) [DrawTexture](Screen-DrawTexture) [DrawTextures](Screen-DrawTextures)
