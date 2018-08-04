# [SuperShapeDemo](SuperShapeDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

Draw [SuperShapes](SuperShapes) with [OpenGL](OpenGL)  
  
This demo computes and displays a 3D supershape using the formula  
found by Gielis (A generic geometric transformation that unifies  
a wide range of natural and abstract shapes. American Journal of  
Botany 90(3):333�338, 2003)  
  
See also http://en.wikipedia.org/wiki/Superformula  
  
"The parameter m relates to the number of symmetries of a shape,  
parameter n1 determines flatness and sharpness of corners and convexity  
of sides. Both parameters n2 and n3 denote whether the shape is inscribed  
or circumscribed in the unit circle." (from  
http://know-center.tugraz.at/download\_extern/papers/ISGI\_SuperShapes\_Lex\_Kienreich.pdf)  
  
You can rotate the shape with the cursor keys.  
  
You can change shape parameters by pressing the keys shown in the demo and  
entering new numeric parameters.  
  
Pressing [ESCape](ESCape) exits the demo.  
  
Please be patient when running this demo. Computation of the supershape and  
its normal vectors and mesh is compute intense and therefore time consuming.  
The only way to speed this up a lot would be to perform most of the computations  
inside of GLSL vertex- and geometry-shaders on the GPU. This advanced exercise  
for now left to the reader.  
  
This demo was written and contributed by Joana Leitao.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SuperShapeDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SuperShapeDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/SuperShapeDemo.m</code>
</div>

