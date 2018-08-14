# [SRGBGammaCorrect](SRGBGammaCorrect)
##### >[Psychtoolbox](Psychtoolbox)>[PsychColorimetric](PsychColorimetric)

RGB = [SRGBGammaCorrect](SRGBGammaCorrect)(rgb,[SCALE])  
  
Gamma correct according to sRGB standard.  
  
SCALE = 0: No scaling applied to input rgb.  Input values \> 1 truncated to 1.  
SCALE = 1: Input data scaled to max of 1.  (Default).  
  
Input values less than 0 are truncated to zero.  
  
The gamma correction stage of the SRGB standard converts inputs in the  
range [0,1] into gamma corrected output in the same range.  
  
This routine then multiplies the [0,1] output by 255 and quantizes  
to integer values.  None-the-less, it still returns the output as  
a double (rather than uint8) matrix.  I (DHB) am not sure this was  
a good design decision, but am for now (6/15/11) leaving it as is  
to avoid breaking code that relies on the current implementation.  
[Smarter, I think would have been to return values in the [0,1] range  
and leave the quantization to the caller, or else to convert to uint8  
after scaling into [0,255].]  
  
See [XYZToSRGBPrimary](XYZToSRGBPrimary) for comment on evolution of the standard  
and of this implementation.  
  
5/1/04    dhb             Wrote it.  
7/8/10    dhb             Updated to match standard I can now find on the web.  
6/15/11   dhb, ms         Clarify input output range issues in comment.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychColorimetric/SRGBGammaCorrect.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychColorimetric/SRGBGammaCorrect.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychColorimetric/SRGBGammaCorrect.m</code>
</div>

