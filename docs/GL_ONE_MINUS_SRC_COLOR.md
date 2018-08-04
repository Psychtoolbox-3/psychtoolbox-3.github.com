# [GL_ONE_MINUS_SRC_COLOR](GL_ONE_MINUS_SRC_COLOR)
##### >[Psychtoolbox](Psychtoolbox)>[PsychAlphaBlending](PsychAlphaBlending)

constantString=GL\_ONE\_MINUS\_SRC\_COLOR  
  
Return the string 'GL\_ONE\_MINUS\_SRC\_COLOR', which specifies an alpha  
blending factor to [Screen](Screen)('BlendFunction', ...).    
  
"Alpha" is a factor which weights RGB values when combining pixels by  
drawing or copying.  Alpha values weight the pixels drawn, the "source  
surface".   Separate alpha values weight the pixels drawn onto, the  
"destination surface".   A given pixel's alpha factor is not necessarily  
the alpha component of that pixel's [rgba] color vector, but may instead  
be the other combined surface's alpha component, a function of either or  
both both alpha compoenents, a constant, or it may derive from RGB values  
of the other combined surface.  The Psychtoolbox command  
[Screen](Screen)('BlendFunction') selects which. It implements the [OpenGL](OpenGL) function  
"glBlendFunc".  
  
In MATLAB, [Screen](Screen)('BlendFunction') accepts strings named for C constants  
passed to the [OpenGL](OpenGL) function glBlendFunc(). Enter "Help  
[PsychAlphaBlending](PsychAlphaBlending)" in the MATLAB command window for a list of blending  
constants (and other functions related to alpha blending).    
  
GL\_ONE\_MINUS\_SRC\_COLOR may only be used as a destination factor, not a  
source factor.  
  
  
see also: [PsychAlphaBlending](PsychAlphaBlending), [AlphaDemo](AlphaDemo), [AlphaBlendingTest](AlphaBlendingTest).  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychAlphaBlending/GL_ONE_MINUS_SRC_COLOR.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychAlphaBlending/GL_ONE_MINUS_SRC_COLOR.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychAlphaBlending/GL_ONE_MINUS_SRC_COLOR.m</code>
</div>

