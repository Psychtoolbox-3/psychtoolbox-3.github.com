# [XYZToSRGBPrimary](XYZToSRGBPrimary)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

[rgb,M] = [XYZToSRGBPrimary](XYZToSRGBPrimary)(XYZ)  
  
Convert between CIE XYZ to sRGB primary  
coordinates.  These are linear device  
coordinates for the primaries of the sRGB  
standard.  If your input is scaled in the  
gamut of the monitor, the numbers will come  
out in the range 0-1.  You may want to scale  
the result into the range 0-1 before applying  
sRGB gamma correction.   
  
Originally implemented from conversion matrix as specified at:  
  http://www.srgb.com/basicsofsrgb.htm  
It turns out this was the draft standard.  The site above is gone  
You can still find the draft standard at:  
  http://www.colour.org/tc8-05/Docs/colorspace/61966-2-1.pdf  
  
I can't find the official technical standard on the web, but  
there is pretty good agreement across web sources.  Wikipedia  
seems fine, as does.  
  http://www.w3.org/Graphics/Color/sRGB  
  
5/1/04  dhb             Wrote it.  
7/8/10    dhb             Updated to match standard I can now find on the web.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/XYZToSRGBPrimary.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/XYZToSRGBPrimary.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/XYZToSRGBPrimary.m</code>
</div>

