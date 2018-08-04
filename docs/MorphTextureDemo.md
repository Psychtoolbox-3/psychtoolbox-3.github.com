# [MorphTextureDemo](MorphTextureDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)>[MorphDemo](MorphDemo)

function [MorphTextureDemo](MorphTextureDemo)([dotson][, normalson][,stereomode][, usefastoffscreenwindows])  
  
[MorphTextureDemo](MorphTextureDemo) -- Demonstrates use of "[moglmorpher](moglmorpher)" for fast morphing  
and rendering of 3D shapes \*and\* textures. See "help [moglmorpher](moglmorpher)" for  
info on moglmorphers purpose and capabilities.  
  
This demo will load two morpheable shapes from OBJ files and two  
textures, then morph them continously into each other, using a simple  
sine-function to define the timecourse of the morph.  
  
Control keys and their meaning: 'a' == Zoom out by moving object away  
from viewer. 'z' == Zoom in by moving object close to viewer. 'k' and 'l'  
== Rotate object around axis. 'ESC' == Quit demo.  
  
### Options:  
  
dotson = If set to 0 (default), just show surface. If set to 1, some dots  
are plotted to visualize the vertices of the underlying mesh. If set to  
2, the mesh itself is superimposed onto the shape. If set to 3 or 4, then  
the projected vertex 2D coordinates are also visualized in a standard  
Matlab figure window.  
  
normalson = If set to 1, then the surface normal vectors will get  
visualized as small green lines on the surface.  
  
stereomode = n. For n\>0 this activates stereoscopic rendering - The shape  
is rendered from two slightly different viewpoints and one of  
Psychtoolbox's built-in stereo display algorithms is used to present the  
3D stimulus. This is very preliminary so it doesn't work that well yet.  
  
usefastoffscreenwindows = If set to 0 (default), work on any graphics  
card. If you have recent hardware, set it to 1. That will enable support  
for fast offscreen windows - and a much faster implementation of shape  
morphing.  
  
This demo and the morpheable OBJ shapes were contributed by Dr. Quoc C.  
Vuong, MPI for Biological Cybernetics, Tuebingen, Germany.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/MorphDemo/MorphTextureDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/MorphDemo/MorphTextureDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/MorphDemo/MorphTextureDemo.m</code>
</div>

