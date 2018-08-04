# [ArrangeRects](ArrangeRects)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRects](PsychRects)

cellRects=[ArrangeRects](ArrangeRects)(n,objectRect,windowRect,[rightToLeft]);  
  
Returns an array of n contiguous rects that achieve a visually   
pleasing arrangement of n objects of size objectRect within a   
window of size windowRect. Each row of the returned matrix is a rect.  
If the rightToLeft argument is supplied and nonzero then  
the cells are ordered right to left (like Hebrew letters).   
Otherwise they are ordered left to right (like English letters).  
The result depends on the proportions of the objectRect, but is   
independent of its size and position.  
Also see [PsychRects](PsychRects).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRects/ArrangeRects.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRects/ArrangeRects.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRects/ArrangeRects.m</code>
</div>

