# [DrawDots3DDemo](DrawDots3DDemo)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[DrawDots3DDemo](DrawDots3DDemo) -- Show fast drawing of 3D dots.  
  
Usage: [DrawDots3DDemo](DrawDots3DDemo)([stereoMode=0][, multiSample=0]);  
  
This demo shows how to use the moglDrawDots3D() function to draw 3D dots  
in [OpenGL](OpenGL) 3D mode. The function is mostly equivalent to  
[Screen](Screen)('DrawDots') for drawing of 2D dots in regular 2D mode.  
  
The first subdemo simply fills the whole 3D scene with uniformly sampled  
random 3D dots, using the special sampling procedure  
[CreateUniformDotsIn3DFrustum](CreateUniformDotsIn3DFrustum)() which was contributed by Diederick  
Niehorster.  
  
The second subdemo shows how to use a GLSL vertex shader on modern GPU's  
to speed up complex drawing of complex 3D dot fields. It shows a nicely  
shaded, slowly rotating "Utah Teapot". Below the teapot is a primitive  
"sparkling fire" of 100 3D dots, which are lit by [OpenGL](OpenGL) and whose  
positions are computed in Matlab/Octave on the CPU. The teapot also emits  
a fountain of colorful particles from its nozzle. This fountain consists  
of 10000 particles, and the particle trajectories are computed on the GPU  
by use of a GLSL vertex shader. Please note that this subdemo may be  
pretty boring, not showing the magic fountain, if your GPU doesn't  
support shaders.  
  
The 3rd subdemo is a speed shootout: It draws the same fountain as demo  
2, but as fast as it can, with sync of display updates to the vertical  
retrace disabled. The fountain is drawn 3 times a 20 seconds duration.  
First with purely Matlab computed trajectories, then with the same shader  
as in demo 2, then again with the shader, but additionally applying  
[OpenGL](OpenGL) display lists to store all data in the fast VRAM of the GPU to  
gain an additional speedup. At the end of these three benchmark runs, the  
demo will end and print out the average redraw rates attainable by the  
three methods. On a modern system with a modern graphics card, you should  
observe quite drastic speedups of GPU+VRAM vs. GPU vs. Matlab/CPU.  
  
The 4th subdemo simulates a "warp-flight" by creating a particle fountain  
that approaches the viewer, expanding while doing so.  
  
  
Btw. if you are a proud owner of a good 3D stereo setup, or at least of  
some anaglyph glasses, you should try the stereo display option as well,  
e.g., stereoMode == 8 for red-blue anaglyphs.  
  
Pressing the [ESCape](ESCape) key continues the demo and progresses to next  
subdemo. Mouse clicks will pause some demos, until another mouse click  
continues the demo.  
  
### Optional parameter:  
  
'stereoMode' if set to a non-zero value, will render at lest the 2nd demo  
in a binocular stereo presentation mode, using the method specified in  
the 'stereoMode' flag. See for example [ImagingStereoDemo](ImagingStereoDemo) for available  
modes.  
  
'multiSample' if set to a non-zero value will enable multi-sample  
anti-aliasing. This however usually doesn't give good results with  
smoothed 3D dots.  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/DrawDots3DDemo.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/DrawDots3DDemo.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/DrawDots3DDemo.m</code>
</div>

