# [OffsetRect](OffsetRect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRects](PsychRects)

newRect = [OffsetRect](OffsetRect)(oldRect,x,y)  
  
Offset the passed rect matrix by the horizontal (x)  
and vertical (y) shift given. You can also pass in column vectors x and y  
with e.g., n different "shifts" and the function will return n copies of  
oldRect, each shifted by one of the shift values in x and y.  
  
Alternatively you can give a single scalar x,y shift value, but apply it  
to a whole matrix of rects 'oldRect' --\> Apply a common offset to a large  
number of rects simultaneously.  
  
Also see [PsychRects](PsychRects).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRects/OffsetRect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRects/OffsetRect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRects/OffsetRect.m</code>
</div>

