# [MakeSineImage](MakeSineImage)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOneliners](PsychOneliners)

 [image] = [MakeSineImage](MakeSineImage)(freqi,freqj,nRowPixels,[nColPixels],[centerRowPixel],[centerColPixel])  
  
 Computes a two-dimensional sine function image.  
  
 The image has dimensions nRowPixels by nColPixels.  
 If nColPixels is omitted, a square image is returned.  
  
 If you want to pass centerRowPixel, you must pass nColPixels.  
 centerRowPixel and centerColPixel each default to zero if not passed.  
  
 8/15/94        dhb     Both row and column dimensions used if passed.  
                dhb     Changed zero frequency convention.  
 6/20/98       dhb, mw Fixed error in zero handling case.  
 9/07/23       dhb     Allow passing of center row and column pixels,  
                       leaving previous behavior unaffected  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOneliners/MakeSineImage.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOneliners/MakeSineImage.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOneliners/MakeSineImage.m</code>
</div>

