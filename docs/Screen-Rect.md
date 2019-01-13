# [Screen('Rect')](Screen-Rect) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

rect=Screen('Rect', windowPointerOrScreenNumber [, realFBSize=0]);

Get local rect of window or screen. This has its top-left corner always at (0,0)  
and encodes the useable size of the window or screen. E.g., in certain stereo  
display modes or other special output modes, the actual useable window area for  
stimulus drawing may be much smaller than the real area occupied by the window.  
Example: In interleaved stereo modes, the effective useable height of a window  
is only half the real height of the window. Use this function to get the actual  
useable drawing area for a window or screen.  
If the optional 'realFBSize' flag is set to 1, then the function returns the  
real size of the windows framebuffer. This is mostly for Psychtoolbox internal  
use, not for regular user-code.  
  


###See also:

