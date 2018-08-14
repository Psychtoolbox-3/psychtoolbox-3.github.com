# [GrowRect](GrowRect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychRects](PsychRects)

r = [GrowRect](GrowRect)(r,horizontalPixels,verticalPixels)  
  
Grows a rect, by subtracting horizontalPixels from the left coordinate  
and verticalPixels from the top coordinate, and adding horizontalPixels  
to the right coordinate and verticalPixels to the bottom coordinate. Also  
see [ScaleRect](ScaleRect). Input can be multiple rects, concatenated into a Mx4  
matrix Using a negate number os pixels to grow by would obviously shrink  
the rect, though be careful as no checks are performed to see if the  
resulting rect is valid.  
  
Also see [PsychRects](PsychRects).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychRects/GrowRect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychRects/GrowRect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychRects/GrowRect.m</code>
</div>

