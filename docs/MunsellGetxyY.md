# [MunsellGetxyY](MunsellGetxyY)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)>[PsychMunsell](PsychMunsell)

[xyY,Xx,trix,Xy,triy,XY,triY] = [MunsellGetxyY](MunsellGetxyY)(angle,value,chroma,munsellData[,Xx,trix,Xy,triy,XY,triY])  
  
Get the xyY coordinates of a specified Munsell renotation by  
interpolating the passed table.  
  
The table should have 6 columns: angle, value, chroma, x, y, Y.  
  
For chroma below 2.0, we interpolate x,y,Y for chroma of 2, and  
then adjust x,y by linear interpolation between chroma 0 and 2,  
using the chromaticity of a zero chroma sample as (0.3101, 0.3162).  
This is the chromaticity of illuminant C.  We think this is right.  
  
11/21/08  dhb, ijk  Wrote it.  
12/01/08  ijk       Added interpolation for low chroma samples.  
          ijk, dhb  Tried to make it go fast by allowing precomputation.  
12/22/08  ijk, dhb  Change y chromaticity of CIE C to .3162, to match standard (was .3163).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGetxyY.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGetxyY.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/PsychMunsell/MunsellGetxyY.m</code>
</div>

