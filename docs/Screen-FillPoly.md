# [Screen('FillPoly')](Screen-FillPoly) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

Screen('FillPoly', windowPtr [,color], pointList [, isConvex]);

Fill polygon. "color" is the clut index (scalar or [r g b] or [r g b a] vector)  
that you want to poke into each pixel; default produces white. "pointList" is a  
matrix: each row specifies the (x,y) coordinates of a vertex.  
The optional flag 'isConvex' allows you to tell the routine if the polygon is  
convex, (value of 1) or if it is concave (value of 0), allowing the routine to  
skip the test for convexity, thereby saving a bit of computation time in timing  
sensitive scripts.  
Drawing filled polygons is a rather compute intense and slow operation. In  
general, drawing convex polygons is pretty fast, drawing concave, but not  
self-intersecting polygons is much slower (\> 30x slower), and drawing concave  
self-intersecting polygons is extremely slow, e.g. \> 2000 times slower. If you  
have to draw very irregular polygons with may points, it might be a good idea to  
preprocess them in some way and maybe break them up into a sequence of more  
convex/regular polygons before submitting them to 'FillPoly'. Or you may want to  
use some custom written drawing function for your purpose which is optimized for  
drawing your type of polygons.   


###See also:
[FramePoly](Screen-FramePoly)
