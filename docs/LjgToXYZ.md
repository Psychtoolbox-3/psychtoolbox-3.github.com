# [LjgToXYZ](LjgToXYZ)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

XYZ = [LjgToXYZ](LjgToXYZ)(Ljg)  
  
Convert OSA Ljg to XYZ (10 degree).  Works by using numerical  
search to invert [XYZToLjg](XYZToLjg).  See [XYZToLjg](XYZToLjg) for details on  
formulae used.  See also [[OSAUCSTest](OSAUCSTest)][(OSAUCSTest)]((OSAUCSTest)).  
  
This can return imaginary values if you pass XYZ values  
that are outside reasonable physical gamut limits.  
  
3/27/01  dhb      Wrote it.  
3/4/05   dhb        Handle new version of optimization toolbox, too.  
9/23/12  dhb, ms  Update options for current Matlab versions.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/LjgToXYZ.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/LjgToXYZ.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/LjgToXYZ.m</code>
</div>

