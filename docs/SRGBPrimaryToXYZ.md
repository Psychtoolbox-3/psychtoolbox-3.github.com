# [SRGBPrimaryToXYZ](SRGBPrimaryToXYZ)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

XYZ = [SRGBPrimaryToXYZ](SRGBPrimaryToXYZ)(rgb)  
  
Convert between sRGB primaries and CIE XYZ.  
The rgb are linear device coordinates for the primaries of the sRGB  
standard.  One would expect these to be in the range 0-1, although  
any scaling will simply propogate through to the XYZ coordinates.  
  
See [XYZToSRGBPrimary](XYZToSRGBPrimary)  
  
5/1/04  dhb  Wrote it.  
7/8/10    dhb  To ensure consistency, get matrix from [XYZToSRGBPrimary](XYZToSRGBPrimary) rather than hard coded here.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/SRGBPrimaryToXYZ.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/SRGBPrimaryToXYZ.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/SRGBPrimaryToXYZ.m</code>
</div>

