# [Screen('FillArc')](Screen-FillArc) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('FillArc',windowPtr,[color],[rect],startAngle,arcAngle)

Draw a filled arc inscribed within the rect. 'color' is the clut index (scalar  
or [r g b a] triplet) that you want to poke into each pixel; default produces  
black with the standard CLUT for this window's pixelSize. Default 'rect' is  
entire window. Angles are measured clockwise from vertical.  


###See also:
[DrawArc](Screen-DrawArc) [FrameArc](Screen-FrameArc)
