# [VRHMDDemo1](VRHMDDemo1)
##### >[Psychtoolbox](Psychtoolbox)>[PsychDemos](PsychDemos)>[OpenGL4MatlabDemos](OpenGL4MatlabDemos)

[VRHMDDemo1](VRHMDDemo1) -- Show 3D stereo display via MOGL [OpenGL](OpenGL) on a VR headset.  
  
This demo shows how to use Psychtoolbox [PsychVRHMD](PsychVRHMD)() driver to display  
stereoscopically rendered 3D scenes on a Virtual Reality head mounted display  
(HMD). The HMD position and orientation is tracked via head tracking, and the  
tracked head pose is used to position the observer in the 3D scene, in this  
case in "Happy teapot land". Obviously, this demo will only work if you have  
one of the supported [HMDs](HMDs) connected to your machine.  
  
Usage: [VRHMDDemo1](VRHMDDemo1)([multiSample=4][, fountain=1][, checkerboard=0][, gpumeasure=0][, debugView=0][, doSeparateEyeRender]);  
  
### Optional parameters:  
  
'multiSample' if set to a non-zero value will enable multi-sample  
anti-aliasing. Can increase quality, but also increases GPU load.  
  
'fountain' if set to 1 will also emit a particle fountain from the nozzle  
of the teapot. Nicer, but higher gpu load.  
  
'checkerboard' if set to 1, show a checkerboard texture instead of the regular  
teapot.  
  
'gpumeasure' if set to 1 will use [Screen](Screen)'s builtin functions for measurement of  
gpu time spent on post-processing the VR images. This excludes actual 3D rendering,  
as time spent between [Screen](Screen)('BeginOpenGL') and [Screen](Screen)('EndOpenGL') won't be measured.  
Note that some VR runtimes have trouble with gpumeasure, as it clashes with their own  
builtin measurement mechanisms, so gpumeasure may cause errors or error messages.  
E.g., a major offender as of December 2022 is the [SteamVR](SteamVR) [OpenXR](OpenXR) runtime, which will  
cause flooding of the console with [OpenGL](OpenGL) error messages - Reason unknown, but was not  
resolvable in hours of work.  
  
'debugView' if set to 1, also display the VR content in a Psychtoolbox onscreen  
window. May impact performance!  
  
'doSeparateEyeRender' if set to 1, perform per eye render passes in an optimized  
order, as recommended by the HMD driver, and query the per eye camera matrices  
individually during each render pass to optimize for head tracking prediction  
accuracy. If set to 0, query matrices for rendering simultaneously for both eyes,  
and render in a potentially non-optimized order. The latter is a bit simpler, but  
potentially less accurate, causing additional motion artifacts. If the setting is  
omitted then the underlying HMD driver will be asked for the optimal value.  
Note that none of the modern VR runtimes supports a doSeparateEyeRender setting of 1  
in any meaningful way. Only the - long dead - original [OculusVR](OculusVR) v0.5 runtime on the  
old Oculus Rift DK1 and DK2 supported this for improved quality. The correct setting  
therefore is always 0 on modern systems, and this is what will be chosen by default.  
  
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

