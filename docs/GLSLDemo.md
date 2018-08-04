# [GLSLDemo](GLSLDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[GLSLDemo](GLSLDemo) - Demonstrate use of the GLSL [OpenGL](OpenGL) Shading language in the  
Psychtoolbox.  
  
The [OpenGL](OpenGL) shading language (GLSL) allows to write specialized programs  
which are uploaded into the graphics hardware itself. These programs  
are then executed very efficiently in the grahpics hardware. So called  
Vertex-Shaders are executed on a per-vertex basis. They calculate and  
manipulate per-vertex properties, e.g., displacement, color, normal  
vectors. So called Fragment-Shaders are executed for each single fragment  
or pixel that is drawn into the backbuffer. They allow, e.g., to implement  
your own lighting model or perform image processing on your image.  
  
GLSL programs are very similar in their syntax to the C programming language,  
its basically C, extended by functions for matrix and vector math and for  
typical graphics purpose.  
  
A specific piece of graphics hardware may only support either vertex-shaders,  
or fragment-shaders or none at all, as these features are pretty new in the  
world of computer-graphics, so this demo may not run at all or at least some  
shaders will either fail or give unexpected results. If you want to make  
use of GLSL you'll need to equip your computer with up to date graphics  
hardware.  
  
This demo loads a collection of shaders. It applies the shaders to a  
collection of objects, demonstrating some visual effects. This is early  
beta code, so don't expect too much. It mostly demonstrates how to get  
started with shader-programming in Psychtoolbox.  
  
Press the 'n' key to toggle between different objects.  
Press the SPACE key to toggle between the different shaders.  
Stop the demo by pressing any other key.  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/GLSLDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/GLSLDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/GLSLDemo.m</code>
</div>

