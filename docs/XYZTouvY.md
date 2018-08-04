# [XYZTouvY](XYZTouvY)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

uvY = [XYZTouvY](XYZTouvY)(XYZ,[compute1960])  
  
Compute chromaticity and luminance from from tristimulus values.  
  
These are u',v' chromaticity coordinates in notation  
used by CIE.  See CIE Colorimetry 2004 publication, or Wyszecki  
and Stiles, 2cd, page 165.  
  
Note that there is an obsolete u,v chromaticity diagram that is similar  
but uses 6 in the numerator for v rather than the 9 that is used for v'.  
See CIE Colorimetry 2004, Appendix A, or Judd and Wyszecki, p. 296.  If  
you want this (maybe to compute correlated color temperatures), you can  
pass this as 1.  It is 0 by default.  
  
See also [uvYToXYZ](uvYToXYZ), [XYZToxyY](XYZToxyY), [xyYToXYZ](xyYToXYZ).  
  
10/31/94  dhb   Wrote it.  
8/24/09   dhb Speed it up a lot by preallocating output.  
6/16/10   dhb More extensive comment.  
5/6/11    dhb Comment fix.  
          dhb Add "compute1960" option.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/XYZTouvY.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/XYZTouvY.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/XYZTouvY.m</code>
</div>

