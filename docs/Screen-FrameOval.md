# [Screen('FrameOval')](Screen-FrameOval) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Draw the outline of an oval inscribed in "rect". "color" is the clut index  
(scalar or [r g b] triplet) that you want to poke into each pixel; default  
produces white with the standard CLUT for this window's pixelSize. Default  
"rect" is entire window.  
Default pen size is (1,1). The penMode argument is ignored. The penWidth must  
equal the penHeight.  If non-equal arguments are given, [FrameOval](FrameOval) will choose  
the maximum value of both. The pen width will be non-uniform for non-circular  
ovals, this is a known limitation.  
Instead of drawing one oval, you can also specify a list of multiple ovals to be  
drawn - this is faster when you need to draw many ovals per frame. To draw n  
ovals, provide "rect" as a 4 rows by n columns matrix, each column specifying  
one oval, e.g., rect(1,5)=left border of 5th oval, rect(2,5)=top border of 5th  
oval, rect(3,5)=right border of 5th oval, rect(4,5)=bottom border of 5th oval.  
If the ovals should have different colors, then provide "color" as a 3 or 4 row  
by n column matrix, the i'th column specifiying the color of the i'th oval.  
If drawing multiple ovals at once, both the penHeight and penMode arguments are  
completely ignored! The penWidth argument defines the size of each drawn oval.  
You can either specify one common penWidth for all ovals, or provide a per-oval  
penWidth.  
  


###See also:
[FillOval](Screen-FillOval)
