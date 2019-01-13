# [Screen('TextBounds')](Screen-TextBounds) 
##### [Psychtoolbox](Psychtoolbox)>[Screen](Screen).{mex*} subfunction

[normBoundsRect, offsetBoundsRect, textHeight, xAdvance] = Screen('TextBounds', windowPtr, text [,x] [,y] [,yPositionIsBaseline] [,swapTextDirection]);

Accepts a window pointer and a 'text' string.  Return in 'normBoundsRect' a rect  
defining the size of the text in units of pixels. Returns in 'offsetBoundsRect'  
offsets of the text bounds from the origin, assuming that the text will be drawn  
at the current position of the text drawing cursor. Only the default high  
quality text renderers return a perfect bounding box. The optionally selectable  
low-quality, fast renderers on Windows and Linux return a bounding box which  
doesn't take letters with descenders into account - Descenders are outside the  
returned box.  
"textHeight" optionally return height of current text string. May return zero if  
this is not supported by the current text renderer.  
"xAdvance" optionally return horizontal advance after drawing the text string.  
May return zero if this is not supported by the current text renderer.  
See help for [Screen](Screen)('DrawText') for info about accepted text string formats and  
all additional parameters...   


###See also:
[DrawText](Screen-DrawText) [TextSize](Screen-TextSize) [TextFont](Screen-TextFont) [TextStyle](Screen-TextStyle) [TextColor](Screen-TextColor) [TextBackgroundColor](Screen-TextBackgroundColor)
