# [GrayIndex](GrayIndex)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

color=[GrayIndex](GrayIndex)(windowPtrOrScreenNumber,[reflectance])  
Returns the CLUT index to produce the specified gray, on a scale of  
0 (black) to 1 (white) at the current screen depth, assuming a  
standard color lookup table for that depth. E.g.  
     gray=[GrayIndex](GrayIndex)(w,0.3);  
     [Screen](Screen)(w,'FillRect',gray);  
  
See [BlackIndex](BlackIndex), [WhiteIndex](WhiteIndex).  
  
No compensation is made for the screen's gamma function. This is  
just a handy way of picking a few grays for simple text and graphics.  
This isn't appropriate for images that need correction for the screen  
gamma.  
  
When the screen is in 1 to 8 bit mode, the Macintosh OS always makes the  
first clut element white and the last black. In 16 or 32 bit mode the  
clut goes from black to white. These CLUT conventions can be overridden  
by [Screen](Screen) 'SetClut', which makes a direct call to the video driver,  
bypassing the Mac OS, allowing you to impose any CLUT whatsoever.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/GrayIndex.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/GrayIndex.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/GrayIndex.m</code>
</div>

