# [AlphaDestinationTerm](AlphaDestinationTerm)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlphaBlending](PsychAlphaBlending)

newDestinationMat=[AlphaDestinationTerm](AlphaDestinationTerm)(destinationFactorStr, sourceMatrix, destinationMatrix)  
  
[AlphaDestinationTerm](AlphaDestinationTerm) simuluates the step of multplying an alpha factor with the  
destination image in [OpenGL](OpenGL) alpha blending.      
  
Apply an [OpenGL](OpenGL) source factor rule such as 'GL\_ZERO' to the image matrix  
'destinationMat', returing the dot product of destinationMat and the  
alpha factor selected by string 'sourceFactor'.    
  
The source image matrix 'sourceMat' is required because destination  
factor strings may select alpha values from the source image.  
  
[AlphaDestinationTerm](AlphaDestinationTerm) calculates with double-precision (64-bit) floating  
point arithmatitic whereas the precision of an [OpenGL](OpenGL) renderer which it  
simulates is unspecified, except that [OpenGL](OpenGL) guarantees perfect precision  
for alpha values 0 and 1 (255 via [Screen](Screen)).  Comparison of  
[AlphaDestinationTerm](AlphaDestinationTerm) with the [OpenGL](OpenGL) renderer shows that alpha  
multiplicaion discards up to one bit of precision.    
  
see also: [AlphaSourceTerm](AlphaSourceTerm), [PsychAlphaBlending](PsychAlphaBlending)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlphaBlending/AlphaDestinationTerm.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlphaBlending/AlphaDestinationTerm.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlphaBlending/AlphaDestinationTerm.m</code>
</div>

