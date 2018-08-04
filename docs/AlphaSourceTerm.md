# [AlphaSourceTerm](AlphaSourceTerm)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlphaBlending](PsychAlphaBlending)

newSourceMat=[AlphaSourceTerm](AlphaSourceTerm)(sourceFactorStr, sourceMat, destinationMat)  
  
[AlphaSourceTerm](AlphaSourceTerm) simuluates the step of multplying an alpha factor with the  
source image in [OpenGL](OpenGL) alpha blending.      
  
Apply an [OpenGL](OpenGL) source factor rule such as 'GL\_ZERO' to the image matrix  
'sourceMat', returing the dot product of sourceMat and the alpha factor  
selected by string 'sourceFactorStr'.    
  
The destination image matrix 'destinationMat' is required because source  
factor strings may select alpha values from the destination.  
  
[AlphaSourceTerm](AlphaSourceTerm) calculates with double-precision (64-bit) floating point  
arithmatitic whereas the precision of an [OpenGL](OpenGL) renderer which it  
simulates is unspecified, except that [OpenGL](OpenGL) guarantees perfect precision  
for alpha values 0 and 1 (255 via [Screen](Screen)).  Comparison of [AlphaSourceTerm](AlphaSourceTerm)  
with the [OpenGL](OpenGL) renderer shows that alpha multiplicaion discards up to  
one bit of precision.    
  
see also: [AlphaDestinationProduct](AlphaDestinationProduct) [PsychAlphaBlending](PsychAlphaBlending)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlphaBlending/AlphaSourceTerm.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlphaBlending/AlphaSourceTerm.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlphaBlending/AlphaSourceTerm.m</code>
</div>

