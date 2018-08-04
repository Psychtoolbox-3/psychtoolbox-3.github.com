# [DrawManuallyAntiAliasedTextDemo](DrawManuallyAntiAliasedTextDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)

[DrawManuallyAntiAliasedTextDemo](DrawManuallyAntiAliasedTextDemo)([textSize=96]) - Manually anti-alias text for special purpose applications.  
  
This demo shows how to draw somewhat anti-aliased text efficiently if you  
can't use the operating systems built-in text anti-aliasing for some  
reason.  
  
It draws the text oversized, without anti-aliasing, into an offscreen  
window. Then it draws the offscreen window into the onscreen window,  
applying alpha-blending and bilinear texture filtering, shrinking to 50%  
size. A GLSL shader based gaussian blur operator is applied during  
drawing to reduce aliasing caused high-frequency edges in the texts  
contour.  
  
This needs a modern graphics card to work and is not as efficient as the  
operating systems anti-aliasing, but still reasonably fast if done right.  
  
see also: [PsychDemos](PsychDemos)  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/DrawManuallyAntiAliasedTextDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/DrawManuallyAntiAliasedTextDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/DrawManuallyAntiAliasedTextDemo.m</code>
</div>

