# [Screen('PanelFitter')](Screen-PanelFitter) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

oldParams = Screen('PanelFitter', windowPtr [, newParams]);

Change operating parameters of builtin panel fitter.  
  
The size of the source framebuffer is given by the 'clientRect' parameter in  
[Screen](Screen)('OpenWindow'), the size of the destination framebuffer is given by the  
'rect' parameter in that function. Default panel fitter behaviour is to rescale  
the source content to completely fit into the destination buffer, something that  
may not preserve aspect-ratio unless care is taken by the user to make sure  
source and destination framebuffer have already the same aspect ratio.  
This function allows to define new src and dst rectangles, thereby implicitely  
defining scaling and filtering properties. It optionally takes new settings in  
'newParams' and returns old settings in 'oldParams'. The function also allows to  
define a rotation angle for rotation of the output image. The parameters are  
11-element vectors of format  
params = [srcX0, srcY0, srcX1, srcY1, dstX0, dstY0, dstX1, dstY1, angle, rotCX,  
rotCY];  
These tuples define top-left and bottom-right (x,y) corners of the source and  
destination rectangles for the (scaled)blit, and the rotation 'angle' if display  
rotation is requested. The angle and rotCX and rotCY parameters are optional and  
assumed to be zero if omitted, ie., no rotation. rotCX and rotCY define the  
center of rotation if a rotation is requested.  
You usually won't call this function directly, but leave the job to a  
higher-level setup routine, e.g., [PsychImaging](PsychImaging)() and its 'UsePanelFitter' setup  
code.  
  
  


###See also:
[OpenWindow](Screen-OpenWindow)
