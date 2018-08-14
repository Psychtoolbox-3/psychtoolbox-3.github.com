# [MakeSincImage](MakeSincImage)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

image =  [MakeSincImage](MakeSincImage)(freq,i0,j0,nRowPixels,[nColPixels])  
  
Computes a two-dimensional sinc function image.  
The sinc function has cut-off frequency freq  
(in cycles/image) and is positioned at (i0,j0).  
  
The image has dimensions nRowPixels by nColPixels.  
If nColPixels is omitted, a square image is returned.  
  
8/15/94     dhb     Added optional column pixels argument.  
10/28/98    dhb     Change to call Matlab sinc rather than my Sinc.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/MakeSincImage.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/MakeSincImage.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/MakeSincImage.m</code>
</div>

