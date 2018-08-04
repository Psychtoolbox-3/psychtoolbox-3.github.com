# [MaskImageOut](MaskImageOut)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlphaBlending](PsychAlphaBlending)

mMasked=[MaskImageOut](MaskImageOut)(m [,alphaIn])  
  
Accept an image matrix "m" and return "nMasked", holding the same image  
but with adjusted alpha values.  [MaskImageOut](MaskImageOut) sets full opacity  
for pixels with value zero and sets full transparency for pixels with  
non-zero value.  
  
If the optional alphaIn argument is specified then [MaskImageIn](MaskImageIn) sets  
zero pixels to alphaIn opacity instad of to full opacity, 255.   
  
see also: [SetImageAlpha](SetImageAlpha), [MaskImageIn](MaskImageIn), [AlphaDemo](AlphaDemo).   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlphaBlending/MaskImageOut.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlphaBlending/MaskImageOut.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlphaBlending/MaskImageOut.m</code>
</div>

