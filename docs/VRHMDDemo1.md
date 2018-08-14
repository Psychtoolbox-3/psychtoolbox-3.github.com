# [VRHMDDemo1](VRHMDDemo1)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[VRHMDDemo1](VRHMDDemo1) -- Show 3D stereo display via MOGL [OpenGL](OpenGL) on a VR headset.  
  
This demo shows how to use Psychtoolbox [PsychVRHMD](PsychVRHMD)() driver to display  
stereoscopically rendered 3D scenes on a Virtual Reality head mounted display  
(HMD). The HMD position and orientation is tracked via head tracking, and the  
tracked head pose is used to position the observer in the 3D scene, in this  
case in "Happy teapot land". Obviously, this demo will only work if you have  
one of the supported [HMDs](HMDs) connected to your machine.  
  
Usage: [VRHMDDemo1](VRHMDDemo1)([doSeparateEyeRender][, multiSample=1][, fountain=1][, checkerboard=0]);  
  
### Optional parameters:  
  
'doSeparateEyeRender' if set to 1, perform per eye render passes in an optimized  
order, as recommended by the HMD driver, and query the per eye camera matrices  
individually during each render pass to optimize for head tracking prediction  
accuracy. If set to 0, query matrices for rendering simultaneously for both eyes,  
and render in a potentially non-optimized order. The latter is a bit simpler, but  
potentially less accurate, causing additional motion artifacts. If the setting is  
omitted then the underlying HMD driver will be asked for the optimal value.  
  
'multiSample' if set to a non-zero value will enable multi-sample  
anti-aliasing. Can increase quality but also increases GPU load.  
  
'fountain' if set to 1 will also emit a particle fountain from the nozzle  
of the teapot. Nicer, but higher gpu load.  
  
Press any key to end the demo.  
  
Plots a timing chart at the end, showing how many milliseconds of GPU processing  
time were needed for each frame. However, these results are often wrong on the  
buggy OSX operating system!  
  
Mouse left/right = Global camera movement left/right.  
Mouse up/down = Global camera movement up/down.  
Mouse up/down + Left mouse button pressed = Global camera movement forward/backward.  
Mouse left/right + Middle or right button pressed: Change looking direction (heading).  
  




<div class="code_header" style="text-align:right;">
  <span style="float:left;">Path&nbsp;&nbsp;</span> <span class="counter">Retrieve <a href=
  "https://raw.github.com/Psychtoolbox-3/Psychtoolbox-3/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/VRHMDDemo1.m">current version from GitHub</a> | View <a href=
  "https://github.com/Psychtoolbox-3/Psychtoolbox-3/commits/beta/Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/VRHMDDemo1.m">changelog</a></span>
</div>
<div class="code">
  <code>Psychtoolbox/PsychDemos/OpenGL4MatlabDemos/VRHMDDemo1.m</code>
</div>

