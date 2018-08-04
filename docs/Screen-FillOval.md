# [Screen('FillOval')](Screen-FillOval) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Fills an ellipse with the given color, inscribed within "rect"."color" is the  
clut index (scalar or [r g b] triplet) that you want to poke into each pixel;  
default produces white with the standard CLUT for this window's pixelSize.  
Default rect is whole window.  
Instead of filling one oval, you can also specify a list of multiple ovals to be  
filled - this is much faster when you need to draw many ovals per frame. To fill  
n ovals, provide "rect" as a 4 rows by n columns matrix, each column specifying  
one oval, e.g., rect(1,5)=left border of 5th oval, rect(2,5)=top border of 5th  
oval, rect(3,5)=right border of 5th oval, rect(4,5)=bottom border of 5th oval.  
If the ovals should have different colors, then provide "color" as a 3 or 4 row  
by n column matrix, the i'th column specifiying the color of the i'th oval.  
The optional parameter 'perfectUpToMaxDiameter' allows to specify the maximum  
diameter in pixels for which a filled oval should look perfect. By default, the  
maximum diameter is chosen to be the full display size, so all ovals will look  
perfect, at a possible speed penalty. If you know your ovals will never be  
bigger than a certain diameter, you can provide that diameter as a hint via  
'perfectUpToMaxDiameter' to allow for some potential speedup when drawing filled  
ovals.   


###See also:
[FrameOval](Screen-FrameOval)
