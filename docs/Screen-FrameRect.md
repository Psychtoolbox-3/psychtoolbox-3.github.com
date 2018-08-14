# [Screen('FrameRect')](Screen-FrameRect) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Draw the outline of a rectangle "rect". "color" is the clut index (scalar or [r  
g b] triplet or [r g b a] quadruple) that you want to poke into each pixel;   
default produces white with the standard CLUT for this window's pixelSize.  
Default "rect" is entire window.  
Instead of framing one rectangle, you can also specify a list of multiple  
rectangles to be framed - this is much faster when you need to draw many  
rectangles per frame. To frame n rectangles, provide "rect" as a 4 rows by n  
columns matrix, each column specifying one rectangle, e.g., rect(1,5)=left  
border of 5th rectange, rect(2,5)=top border of 5th rectangle, rect(3,5)=right  
border of 5th rectangle, rect(4,5)=bottom border of 5th rectangle. If the  
rectangles should have different colors, then provide "color" as a 3 or 4 row by  
n column matrix, the i'th column specifiying the color of the i'th rectangle.  
You can also specify a single pen size or a vector pen sizes (one for each  
rectangle) to control the thickness of the lines used to frame the rect. Default  
"penWidth" is 1 pixel unit.   


###See also:
[FillRect](Screen-FillRect)
