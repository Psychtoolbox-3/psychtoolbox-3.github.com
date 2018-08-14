# [Screen('TextTransform')](Screen-TextTransform) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction


Query or assign a 2D matrix defining a 2D affine transformation to apply to  
drawn text.  
'windowPtr' is the handle to the window for which the affine transform should be  
assigned or queried.  
'newMatrix' is an optional new 2x3 affine transformation matrix to assign.  
'oldMatrix' is the currently assigned 2x3 affine transformation matrix.  
The first 2 columns encode the 2x2 matrix, the 3rd column encodes tx, ty  
translation:  
[ xx, xy, tx ]  
[ yx, yy, ty ]  
  
The affine transformation matrix defaults to an identity transformation matrix,  
in other words, no affine transformation is applied to a window by default.  
Not all text renderers do support application of affine transformations to text.  
If a renderer does not support affine transformations then the selected affine  
transformation is silently ignored during text drawing. As of February 2016 only  
the standard FTGL text renderer supports affine transforms in a meaningful way.  
The legacy Apple OSX [CoreText](CoreText) renderer only supports transforms in a somewhat  
broken and limited manner, at drastically reduced performance.  
The precision of text bounding boxes as returned by [Screen](Screen)('TextBounds') may be  
impaired if non-identity affine transformations are applied. Text positioning  
may also be impaired. Different text renderers may provide inconsistent results  
wrt. text positioning and bounding boxes.  
In most cases it is better to use the general geometric stimulus post-processing  
of the Psychtoolbox image processing pipeline to apply geometric transformations  
to text and other visual content. This allows you to work in an easy to  
understand coordinate frame, with accurate text positioning, bounding boxes etc.  
and apply a consistent transformation to both text and other visual stimulus  
content as a post-processing step.  
  


###See also:
[TextBounds](Screen-TextBounds) [TextSize](Screen-TextSize) [TextFont](Screen-TextFont) [TextStyle](Screen-TextStyle) [TextColor](Screen-TextColor) [TextBackgroundColor](Screen-TextBackgroundColor) Preference
