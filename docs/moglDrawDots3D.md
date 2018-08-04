# [moglDrawDots3D](moglDrawDots3D)
##### >[Psychtoolbox](Psychtoolbox)>[PsychOpenGL](PsychOpenGL)

Draw a large number of dots in 3D very efficiently.  
  
Usage: moglDrawDots3D(windowPtr, xyz [,dotdiameter] [,dotcolor] [,center3D] [,dot\_type] [, glslshader]);  
  
This function is the 3D equivalent of the [Screen](Screen)('DrawDots') subfunction  
for fast drawing of 2D dots. It has mostly the same paramters as that  
function, but extended into the 3D domain. It accepts a subset of the  
parameters for that function, ie., it is less liberal in what it accepts,  
in order to allow for simpler code and maximum efficiency.  
  
As a bonus, it accepts one additional parameter 'glslshader', the  
optional handle to a GLSL shading program, e.g., as loaded from  
filesystem via [LoadGLSLProgram](LoadGLSLProgram)().  
  
The routine will draw into the 3D [OpenGL](OpenGL) userspace rendering context of  
onscreen window or offscreen window (or texture) 'windowPtr'. It will  
automatically switch to that window if it isn't already active in 3D  
mode, and it will restore the drawing target to whatever was set before  
invocation in whatever mode (2D or 3D). This is a convenience feature for  
lazy users that mostly draw in 2D. If you intend to draw more stuff in 3D  
for a given frame, then you should switch your targetwindow 'windowPtr'  
into 3D mode manually via [Screen](Screen)('BeginOpenGL') yourself beforehand. This  
will avoid redundant and expensive context switches and increase the  
execution speed of your code!  
  
### Parameters and their meaning:  
  
'windowPtr' Handle of window or texture to draw into.  
'xyz' A 3-by-n or 4-by-n matrix of n dots to draw. Each column defines  
one dot to draw, either as 3D position (x,y,z) or 4D position (x,y,z,w).  
Must be a double matrix!  
  
'dotdiameter' optional: Either a single scalar spec of dot diameter, or a  
vector of as many dotdiameters as dots 'n', or left out. If left out, a  
dot diameter of 1.0 pixels will be used. Drawing of dots of different  
sizes is much less efficient than drawing of dots of identical sizes! Try  
to group many dots of identical size into separate calls to this function  
for best performance!  
  
'dotcolor' optional: Either a 3 or 4-component [R,G,B] or [R,G,B,A] color  
touple with a common drawing color, or a 3-by-n or 4-by-n matrix of  
colors, one [R;G;B;A] column for each individual dot. A common color for  
all dots is faster.  
  
'dot\_type' optional: A setting of zero will draw rectangular dots, a  
setting of 1 will draw round dots, a setting of 2 will draw round dots of  
extra high quality if the hardware supports that. For anti-aliased dots  
you must select a setting of 1 or 2 and enable alpha blending as well.  
  
'glslshader' optional: If omitted, shading state is not changed. If set  
to zero, then the standard fixed function [OpenGL](OpenGL) pipeline is used, like  
in [Screen](Screen)('DrawDots') (under most circumstances). If a positive  
glslshader handle to a GLSL shading program object is provided, that  
shader program will be used. You can use this, e.g., to bind a custom vertex  
shader to perform complex per-dot calculations very fast on the GPU.  
  
See   




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychOpenGL/moglDrawDots3D.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychOpenGL/moglDrawDots3D.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychOpenGL/moglDrawDots3D.m</code>
</div>

