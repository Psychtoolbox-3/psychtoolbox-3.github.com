# [Screen('WindowSize')](Screen-WindowSize) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[width, height]=Screen('WindowSize', windowPointerOrScreenNumber [, realFBSize=0]);

Return the width and height of a window or screen in units of pixels.  
By default, the useable size in pixels is returned, ie., the size of the area  
usercode can draw to. If the optional 'realFBSize' flag is set to 1, the real  
size of the windows framebuffer is returned. Those sizes can differ, e.g.,  
because certain stereo display modes or high color precision display modes  
require adjustments. The 'realFBSize' 1 setting is mostly for Psychtoolbox  
internal use, not for regular user-code.  
  


###See also:
Screen('Rect')
