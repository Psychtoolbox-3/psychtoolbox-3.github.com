# [uvToxy](uvToxy)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

xy = [uvToxy](uvToxy)(uv,[compute1960])  
  
Convert CIE u'v' chromaticity to CIE xy chromaticity.  
  
These are u',v' chromaticity coordinates in notation  
used by CIE.  See CIE Colorimetry 2004 publication, or Wyszecki  
and Stiles, 2cd, page 165.  
  
Note that there is an obsolete u,v chromaticity diagram that is similar  
but uses 6 in the numerator for u rather than the 9 that is used for u'.  
See CIE Coloimetry 2004, Appendix A, or Judd and Wyszecki, p. 296. If  
you want this (maybe to compute correlated color temperatures), you can  
pass this as 1.  It is 0 by default.  
  
See also [uvYToXYZ](uvYToXYZ), [XYZTouvY](XYZTouvY), [xyTouv](xyTouv)  
  
7/15/03  dhb, bx  Wrote it.  
3/17/04  dhb      Fixed typos.  This must not have been tested previously.  
5/06/11  dhb      Improve comment, optional 1960 computations  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/uvToxy.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/uvToxy.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/uvToxy.m</code>
</div>

