# [SetSourceAlpha](SetSourceAlpha)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlphaBlending](PsychAlphaBlending)

[newSourceMat, newDestinationMat]=[SetSourceAlpha](SetSourceAlpha)[(SourceFactorStr]((SourceFactorStr), alpha, sourceImage, destinationImage)  
  
Given an alpha blending factor, "sourceFactorStr", insert "alpha"  
into the source or destination image such that on alpha blending with the  
specified sourceFactorStr "alpha" is selected as the destination  
alpha.  
  
For some combinations of destination factor string and source factor  
string, [SetSourceAlpha](SetSourceAlpha) may undo a subsequent call to [SetDestinationAlpha](SetDestinationAlpha)  
or be undone by a previous call to [SetDestinationAlpha](SetDestinationAlpha).  This happens  
when both the destination factor string and the source factor string  
specify the same location of alpha values yet store different alpha  
values.  For example, if both the source alpha and destination alpha are  
drawn from the source alpha plane (GL\_SRC\_ALPHA)  then setting the source  
alpha to 0 would also change the destination alpha to 0.  Both source and  
destination surfaces would share the source surface alpha plane for  
storage of the alpha value.   
  
[SetAlphaDestination](SetAlphaDestination) helps test [OpenGL](OpenGL) alpha blending precision.          
  
see also: [PsychAlphaBlending](PsychAlphaBlending)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlphaBlending/SetSourceAlpha.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlphaBlending/SetSourceAlpha.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlphaBlending/SetSourceAlpha.m</code>
</div>

